---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-title: 時間指定メタデータ追加通知のリスナー
title: 時間指定メタデータ追加通知のリスナー
uuid: 419f4204-e3c3-4608-beb4-4cd259c8474d
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# 時間指定メタデ追加ータ通知{#add-listeners-for-timed-metadata-notifications}のリスナー

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。

関連するアクティビティをアプリケーションに通知する次のイベントをリッスンすると、時間指定メタデータを監視できます。

* `MediaPlayerItemEvent.ITEM_CREATED`:オブジェクトの初期リストは、 `TimedMetadata` オブジェクトの作成後 `MediaPlayerItem` に使用できます。

   このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_UPDATED`:マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストにカスタムタグが追加される場合があるので、追加の `TimedMetadata` オブジェクトが `MediaPlayerItem.timedMetadata` プロパティに追加される可能性があります。

   このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`:新しい `TimedMetadata` オブジェクトが作成されるたびに、このイベントがMediaPlayerによってディスパッチされます。

   初期化フェーズ中に作成された`TimedMetadata`オブジェクトに対しては、このイベントはディスパッチされません。

1. 適切なリスナーを実装します。

   ```
   private function onItemCreated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onItemUpdated(event:MediaPlayerItemEvent):void { 
       var timedMetadataCollection:Vector.<TimedMetadata> = event.item.timedMetadata; 
       // process the timed metadata collection 
   } 
   
   private function onTimedMetadataAvailable(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       // process timed metadata 
   }
   ```

1. イベントリスナーを登録します。

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
   player.addEventListener(TimedMetadataEvent.TIMED_METADATA_AVAILABLE,  
                           onTimedMetadataAvailable);
   ```

ID3メタデータは、同じ`TimedMetadataEvent.TIMED_METADATA_AVAILABLE`を通じてディスパッチされます。 ただし、TimedMetadataオブジェクトの`type`プロパティを使用してTAGとID3を区別できるので、混乱の原因になりません。 ID3タグについて詳しくは、[ID3タグ](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md)を参照してください。