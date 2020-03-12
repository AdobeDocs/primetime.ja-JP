---
description: メディアコンテンツがライブかVODかを知る必要がある場合があります。
seo-description: メディアコンテンツがライブかVODかを知る必要がある場合があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: 5455801e-b5eb-4829-bde6-ef4440cd69c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# コンテンツがライブかVODかの識別{#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブかVODかを知る必要がある場合があります。

1. ブラウザーTVSDKがイベントをトリガ `AdobePSDK.PSDKEventType.STATUS_CHANGED` ーするまで待 `event.status` ちます `AdobePSDK.MediaPlayerStatus.PREPARED`。

   この手順により、メディアリソースが正常に読み込まれたことを確認します。

   >[!IMPORTANT]
   >
   >ブラウザーTVSDKが少なくともその状態でない場 `PREPARED``IllegalStateException`合、以下のメソッドを呼び出そうとすると、

1. インターフ `live` ェイスから読み `MediaPlayerItem` 取ります。

   ```js
   player.currentItem.live
   ```

