---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
seo-description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
seo-title: カスタムコンテンツリゾルバーの実装
title: カスタムコンテンツリゾルバーの実装
uuid: cf85dd90-242e-4f9e-9785-158ca0fc9465
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# カスタムコンテンツリゾルバーの実装{#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

ブラウザーTVSDKは、新しいオポチュニティを検出すると、登録されたコンテンツリゾルバーを繰り返し処理し、このメソッドを使用してそのオポチュニティを解決できるリゾルバーを探 `canResolve` します。 trueを最初に返したものが、オポチュニティの解決に選択されます。 使用できるコンテンツリゾルバーがない場合、そのオポチュニティはスキップされます。 コンテンツ解決プロセスは通常非同期なので、コンテンツリゾルバーは、プロセスが完了した時点でブラウザーTVSDKに通知する必要があります。

次の情報を記憶しておきます。

* コンテンツリゾルバーは、TVSDK `client.process` が実行する必要のあるタイムライン操作を指定するために呼び出します。

   この操作は通常、広告の時間の配置です。

* コンテンツリゾルバーは、解 `client.notifyCompleted` 決プロセスが成功した場合、またはプロセスが失 `client.notifyFailed` 敗した場合に呼び出します。

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

   UIフレームワークプレーヤーでは、次のようにカスタムコンテンツファクトリを指定できます。

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

