---
description: メディアコンテンツがライブか VOD かを知る必要が生じる場合があります。
title: コンテンツがライブか VOD かを識別します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---

# コンテンツがライブか VOD かを識別します{#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブか VOD かを知る必要が生じる場合があります。

1. ブラウザー TVSDK がトリガーするのを待つ `AdobePSDK.PSDKEventType.STATUS_CHANGED` イベント `event.status` / `AdobePSDK.MediaPlayerStatus.PREPARED`.

   この手順では、メディアリソースが正常に読み込まれたことを確認します。

   >[!IMPORTANT]
   >
   >ブラウザー TVSDK が `PREPARED` 状態、次のメソッドを呼び出そうとすると、 `IllegalStateException`.

1. 読み取り `live` から `MediaPlayerItem` インターフェイス：

   ```js
   player.currentItem.live
   ```
