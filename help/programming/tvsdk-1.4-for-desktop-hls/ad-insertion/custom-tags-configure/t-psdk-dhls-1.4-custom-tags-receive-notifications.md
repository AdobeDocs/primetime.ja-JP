---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。
title: 時間指定メタデータ通知のリスナーを追加する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 時間指定メタデータ通知のリスナーを追加する{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。

時間指定メタデータを監視するには、次のイベントをリッスンします。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_CREATED`：の最初のリスト `TimedMetadata` オブジェクトは、 `MediaPlayerItem` が作成されました。

  このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_UPDATED`：マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される可能性があります。そのため、追加の `TimedMetadata` オブジェクトが `MediaPlayerItem.timedMetadata` プロパティ。

  このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`：新しい `TimedMetadata` オブジェクトが作成された場合、このイベントは MediaPlayer によってディスパッチされます。

  このイベントは、 `TimedMetadata` オブジェクトが初期化フェーズ中に作成されました。

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

ID3 メタデータが同じ `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`. ただし、TimedMetadata オブジェクトの `type` プロパティを使用して TAG と ID3 を区別します。 ID3 タグについて詳しくは、 [ID3 タグ](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md).
