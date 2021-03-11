---
description: 独自のオポチュニティディテクターを実装できます。
title: カスタムオポチュニティディテクターの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# カスタムオポチュニティディテクターの実装{#implement-a-custom-opportunity-detector}

独自のオポチュニティディテクターを実装できます。

* オポチュニティジェネレーターが、現在のメディアストリームに関連付けられた`TimedMetadata`オブジェクトに基づいている場合は、`SpliceOutOpportunityGenerator`または`TimedMetadataOpportunityGenerator`を拡張する必要があります。

* オポチュニティジェネレーターが、外部サービス（CISなど）が提供する帯域外データに基づいている場合は、`OpportunityGenerator`を拡張する必要があります。

1. カスタムオポチュニティジェネレーターを作成します。

       カスタムオポチュニティジェネレーターが&#39;TimedMetadata&#39;オブジェクトに基づいている場合は、&#39;TimedMetadataOpportunityGenerator&#39;を拡張し、以下のメソッドをオーバーライドします。
   
   * `doConfigure`  — このメソッドは、メディアプレイヤーアイテムが作成された後に呼び出され、必要に応じてオポチュニティの初期セットを作成するオポチュニティジェネレーターを提供します
   * `doProcess`  — このメソッドは、新しい情報 `TimedMetadata` が検出されるたびに呼び出されます（例えば、ライブ/リニアストリームの場合は、プレイリスト/マニフェストが更新されるたびに）

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

1. 再生するメディアストリーム用のカスタムコンテンツファクトリを登録します。

   ```
   var mediaPlayerItemConfig:MediaPlayerItemConfig = new DefaultMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomContentFactory(); 
   ... 
   
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

