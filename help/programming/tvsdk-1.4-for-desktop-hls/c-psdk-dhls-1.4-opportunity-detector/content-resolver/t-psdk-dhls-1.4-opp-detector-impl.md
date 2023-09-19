---
description: 独自のオポチュニティディテクターを実装できます。
title: カスタムオポチュニティディテクターの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# カスタムオポチュニティディテクターの実装{#implement-a-custom-opportunity-detector}

独自のオポチュニティディテクターを実装できます。

* オポチュニティジェネレーターが `TimedMetadata` 現在のメディアストリームに関連付けられているオブジェクト。その場合は、 `SpliceOutOpportunityGenerator` または `TimedMetadataOpportunityGenerator`.

* オポチュニティジェネレーターが、外部サービス（CIS など）が提供する帯域外データに基づいている場合、 `OpportunityGenerator`.

1. カスタムオポチュニティジェネレーターを作成します。

       カスタムオポチュニティジェネレーターが「TimedMetadata」オブジェクトに基づいている場合は、「TimedMetadataOpportunityGenerator」を拡張し、次のメソッドを上書きします。
   
   * `doConfigure`  — このメソッドは、メディアプレーヤーアイテムが作成された後に呼び出され、必要に応じて、オポチュニティの初期セットを作成するオポチュニティジェネレーターを提供します
   * `doProcess`  — このメソッドは、新しくなるたびに呼び出されます `TimedMetadata` が検出されます（例えば、プレイリスト/マニフェストが更新されるたびにライブ/リニアストリームの場合）。

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

1. カスタムオポチュニティジェネレーターを使用するカスタムコンテンツファクトリを作成します。

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
