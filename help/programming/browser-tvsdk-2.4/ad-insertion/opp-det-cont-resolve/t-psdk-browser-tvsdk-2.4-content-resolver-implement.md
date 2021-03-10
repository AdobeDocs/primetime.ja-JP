---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
title: カスタムコンテンツリゾルバーの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---


# カスタムコンテンツリゾルバーの実装{#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

ブラウザーTVSDKは、新しいオポチュニティを検出すると、`canResolve`メソッドを使用して、そのオポチュニティを解決できるコンテンツリゾルバーを探します。 trueを最初に返したコンテンツは、オポチュニティの解決に選択されます。 オポチュニティを解決できるコンテンツリゾルバーがない場合、そのオポチュニティはスキップされます。 通常、コンテンツ解決プロセスは非同期的なので、コンテンツリゾルバーは、プロセスが完了したことをブラウザーTVSDKに通知する必要があります。

次の情報を覚えておいてください。

* コンテンツリゾルバーは`client.process`を呼び出して、TVSDKが実行する必要のあるタイムライン操作を指定します。

   この操作は、通常、広告の時間を配置します。

* コンテンツリゾルバーは、解決プロセスが成功した場合は`client.notifyCompleted`を呼び出し、失敗した場合は`client.notifyFailed`を呼び出します。

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

1. カスタムコンテンツリゾルバーを使用する、カスタムコンテンツファクトリを作成します。

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

1. 再生するメディアストリーム用のカスタムコンテンツファクトリを登録します。

   UI Frameworkプレーヤーでは、次のようにカスタムコンテンツファクトリを指定できます。

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

