---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
title: カスタムコンテンツリゾルバーの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# カスタムコンテンツリゾルバーの実装{#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

ブラウザー TVSDK は、新しいオポチュニティを検出すると、登録されているコンテンツリゾルバーを繰り返し処理し、 `canResolve` メソッド。 オポチュニティの解決のために、最初に true を返したものが選択されます。 可能なコンテンツリゾルバーがない場合は、そのオポチュニティはスキップされます。 通常、コンテンツ解決プロセスは非同期なので、コンテンツリゾルバーは、プロセスが完了したときにブラウザー TVSDK に通知します。

次の情報に留意してください。

* コンテンツリゾルバーが `client.process` を使用して、TVSDK が実行する必要のあるタイムライン操作を指定します。

  操作は通常、広告ブレークの配置です。

* コンテンツリゾルバーが `client.notifyCompleted` 解決プロセスが成功した場合、または `client.notifyFailed` （プロセスが失敗した場合）

1. カスタムオポチュニティリゾルバーを作成します。

   ```js
   /** 
     * Class implementing AdobePSDK.ContentResolver interface  
   */ 
   CustomResolver = function () { 
   }; 
   
   CustomResolver.prototype = { 
       constructor: CustomResolver, 
       configureCallbackFunc: function (item, client) { 
       // here you can read any media stream characteristics which 
       // might help configure your content resolver like 
       // - the media player item configuration through the item.config 
       // - the media resource metadata through item.resource.metadata 
      }, 
   
       canResolveCallbackFunc: function (opportunity) { 
       // check if the opportunity can be resolved by this resolver 
       // if yes return true, otherwise return false 
       return true; 
      }, 
   
       resolveCallbackFunc: function (opportunity) {         
       // start the resolving process 
       // communicate with your custom ad server 
   
       // in this example we assume that: 
       // - if successful, onResolveCompleted method will be invoked 
       // - if failed, onResolveFailed method will be invoked 
      }, 
   
       onResolveCompleted: function (response) { 
        try { 
           var proposals = []; 
           // extract the timeline ad placement from the response 
           // and add them to the proposal vector 
           // - extract the ad break 
           // - calculate the placement (can reuse the _opportunity.placement) 
           // var timelineOperation = new AdobePSDK.AdBreakPlacement (adBreak, placement); 
           // proposals.push (timelineOperation); 
   
           client.process (proposals); 
           client.notifyCompleted (_opportunity); 
       } catch (error) { 
           onResolveFailed (error); 
       } 
   }, 
   
       onResolveFailed: function (error) { 
         client.notifyFailed (_opportunity); 
       } 
   
   }; 
   ```

1. カスタムコンテンツリゾルバーを使用するカスタムコンテンツファクトリを作成します。

   例：

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
       constructor: CustomContentFactory, 
       retrieveResolversCallbackFunc: function (item) { 
           var result = []; 
           var resource = item.resource; 
           if (resource.metadata.containsKey("custom-opportunity-detector")) { 
               result.push (new CustomResolver()); 
           } 
           return result; 
       }, 
       … 
   }; 
   ```

1. 再生するメディアストリームのカスタムコンテンツファクトリを登録します。

   UI Framework Player では、次のようにカスタムコンテンツファクトリを指定できます。

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var advertisingMetadata = new AdobePSDK.AdvertisingMetadata(); 
   // set any parameter you need for custom ad resolver 
   // advertisingMetadata.setValue ("customparam", "customvalue"); 
   
   var metadata = new AdobePSDK.Metadata(); 
   metadata.setMetadata ("custom-opportunity-detector", advertisingMetadata); 
   
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
       mediaPlayerItemConfig: { 
              advertisingFactory: advertisingFactory 
       }, 
          mediaResource: { 
                  resourceUrl:'Specify Resource Url', 
                  metadata: metadata 
          } 
   } 
   
   }); 
   ```
