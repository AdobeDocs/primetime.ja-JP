---
description: OpportunityGenerator インターフェイスを拡張して、独自のオポチュニティジェネレーターを実装できます。
title: カスタムオポチュニティジェネレーターの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# カスタムオポチュニティジェネレーターの実装{#implement-a-custom-opportunity-generator}

OpportunityGenerator インターフェイスを拡張して、独自のオポチュニティジェネレーターを実装できます。

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

1. カスタムオポチュニティジェネレーターを使用するカスタムコンテンツファクトリを作成します。

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

1. 再生するメディアストリームのカスタムコンテンツファクトリを登録します。

   UI Framework Player では、次のようにカスタムコンテンツファクトリを指定できます。

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
