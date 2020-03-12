---
description: 独自のオポチュニティディテクターを実装できます。
seo-description: 独自のオポチュニティディテクターを実装できます。
seo-title: カスタムオポチュニティディテクターの実装
title: カスタムオポチュニティディテクターの実装
uuid: 18fb431b-4585-4293-92a7-b77ab7f9b7db
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# カスタムオポチュニティディテクターの実装{#implement-a-custom-opportunity-detector}

独自のオポチュニティディテクターを実装できます。

* オポチュニティジェネレーターが、現在のメデ `TimedMetadata` ィアストリームに関連付けられたオブジェクトに基づいている場合は、またはを拡張する必要 `SpliceOutOpportunityGenerator` がありま `TimedMetadataOpportunityGenerator`す。

* オポチュニティジェネレーターが、外部サービス（CISなど）が提供する帯域外データに基づいている場合は、を拡張する必要がありま `OpportunityGenerator`す。

1. カスタムオポチュニティジェネレーターを作成します。

       カスタムオポチュニティジェネレーターが&#39;TimedMetadata&#39;オブジェクトに基づいている場合は、&#39;TimedMetadataOpportunityGenerator&#39;を拡張し、次のメソッドをオーバーライドします。
   
   * `doConfigure`  — このメソッドは、メディアプレイヤーアイテムの作成後に呼び出され、必要に応じてオポチュニティの初期セットを作成するオポチュニティジェネレーターを提供します
   * `doProcess`  — このメソッドは、新しいデータが検出されるた `TimedMetadata` びに（例えば、ライブ/リニアストリームの場合、プレイリスト/マニフェストが更新されるたびに）呼び出されます。

   ```
   public class CustomOpportunityGenerator extends TimedMetadataOpportunityGenerator { 
       override protected function doConfigure(playhead:Number, playbackRange:TimeRange):void { 
           // the playhead represents the initial playback position 
           // the playback range represents the initial playback range 
   
           // the item property indicates the current MediaPlayerItem associated with this generator 
           // the initial set of timed metadata can be obtain through the item property 
           var timedMetadataCollection:Vector.<TimedMetadata> = item.timedMetadata; 
       } 
   
       override protected function doProcess(timedMetadata:TimedMetadata):void { 
           ... 
   
           // when an opportunity is created by this generator 
           // we need to notify the TVSDK through the client property 
           client.resolve(opportunity); 
       }  
       ... 
   }
   ```

1. カスタムオポチュニティジェネレーターを使用する、カスタムコンテンツファクトリを作成します。

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       ... 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
           var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
           result.push(new CustomOpportunityGenerator()); 
   
           return result; 
       } 
   }
   ```

1. 再生するメディアストリームのカスタムコンテンツファクトリを登録します。

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

