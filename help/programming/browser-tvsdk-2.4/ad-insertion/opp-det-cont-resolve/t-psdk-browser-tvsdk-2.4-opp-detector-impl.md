---
description: OpportunityGeneratorインターフェイスを拡張して、独自のオポチュニティジェネレーターを実装できます。
title: カスタムオポチュニティジェネレーターの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 5%

---


# カスタムオポチュニティジェネレーターの実装{#implement-a-custom-opportunity-generator}

OpportunityGeneratorインターフェイスを拡張して、独自のオポチュニティジェネレーターを実装できます。

1. カスタムオポチュニティジェネレーターを作成します。

   例：

   ```js
   /** 
   * Class implementing AdobePSDK.OpportunityGenerator interface 
   */ 
   CustomOpportunityGenerator = function () { 
   }; 
   
   CustomOpportunityGenerator.prototype = { 
       constructor: CustomOpportunityGenerator, 
       configureCallbackFunc: function (item, client, mode, playhead, playbackRange) {  
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current AdobePSDK.MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadatas = item.timedMetadata; 
       }, 
       updateCallbackFunc: function (playhead, playbackRange) { 
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve (opportunity); 
       }, 
       … 
   }; 
   ```

1. カスタムオポチュニティジェネレーターを使用する、カスタムコンテンツファクトリを作成します。

   例：

   ```js
   /** 
     * Class implementing AdobePSDK.ContentFactory interface 
   */ 
   CustomContentFactory = function () { 
   }; 
   
   CustomContentFactory.prototype = { 
          constructor: CustomContentFactory, 
          retrieveOpportunityGeneratorsCallbackFunc: function (item) { 
               var result = []; 
               result.push (new CustomOpportunityGenerator()); 
               return result; 
       }, 
       … 
   }; 
   ```

1. 再生するメディアストリーム用のカスタムコンテンツファクトリを登録します。

   UI Frameworkプレーヤーでは、次のようにカスタムコンテンツファクトリを指定できます。

   ```js
   var advertisingFactory = new CustomContentFactory(); 
   var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
           mediaPlayerItemConfig: { 
                   advertisingFactory: advertisingFactory 
           }, 
               mediaResource: { 
                   resourceUrl:'Specify Resource Url' 
          } 
     } 
   }); 
   ```

