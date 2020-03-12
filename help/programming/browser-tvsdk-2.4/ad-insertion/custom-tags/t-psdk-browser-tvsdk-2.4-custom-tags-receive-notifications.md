---
description: マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。
seo-description: マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。
seo-title: 時間指定メタデータ通知のリスナーの追加
title: 時間指定メタデータ通知のリスナーの追加
uuid: c82c5549-0ab6-4343-a766-5176e784d4cb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 時間指定メタデータ通知のリスナーの追加{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、AdobePSDK.TimedMetadataEventをリッスンします。

新しいオブジェクト `TimedMetadata` が作成されると、MediaPlayerがディスパッチしま `AdobePSDK.TimedMetadataEvent`す。

1. 適切なリスナーを実装します。

   ```js
   function onTimedMetadataEvent(event) { 
       var timedMetadata = event.timedMetadata; 
       // process the timed metadata collection 
       } 
   ```

1. イベントリスナーを登録します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE, onTimedMetadataEvent);
   ```

ID3メタデータは、同じメソッドを通じてディスパッチされま `Events.TimedMetadataEvent`す。 このプロパティを使 `timedMetadata.type` 用して、TAGとID3を区別できます。

