---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。
seo-title: 時間指定メタデータ通知のリスナーの追加
title: 時間指定メタデータ通知のリスナーの追加
uuid: 419f4204-e3c3-4608-beb4-4cd259c8474d
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 時間指定メタデータ通知のリスナーの追加{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを登録します。

次のイベントをリッスンして、時間指定メタデータを監視できます。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_CREATED`:オブジェクトの初期リ `TimedMetadata` ストは、を作成した後で使 `MediaPlayerItem` 用できます。

   このイベントは、このような場合にアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_UPDATED`:マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される可能性があるので、プロパティに追加のオ `TimedMetadata` ブジェクトが追加される場合が `MediaPlayerItem.timedMetadata` あります。

   このイベントは、このような場合にアプリケーションに通知します。

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`:新しいオブジェクトが作 `TimedMetadata` 成されるたびに、このイベントがMediaPlayerによってディスパッチされます。

   このイベントは、初期化段階で作成され `TimedMetadata` たオブジェクトに対してはディスパッチされません。

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

ID3メタデータは、同じメソッドを通じてディスパッチされま `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`す。 ただし、TimedMetadataオブジェクトのプロパティを使用してTAGとID3を区別できるので、こ `type` れによって混乱が生じることはありません。 ID3タグについて詳しくは、 [ID3タグを参照してください](../../../tvsdk-1.4-for-desktop-hls/r-psdk-dhls-1.4-notification-system/notification-system/t-psdk-dhls-1.4-id3-metadata-retrieve.md)。