---
description: メディアコンテンツがライブかVODかを知る必要がある場合があります。
seo-description: メディアコンテンツがライブかVODかを知る必要がある場合があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: 5455801e-b5eb-4829-bde6-ef4440cd69c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# コンテンツがライブかVOD{#identify-whether-the-content-is-live-or-vod}かを識別します。

メディアコンテンツがライブかVODかを知る必要がある場合があります。

1. ブラウザーTVSDKが`AdobePSDK.PSDKEventType.STATUS_CHANGED`イベントをトリガーするまで待ちます（`event.status`は`AdobePSDK.MediaPlayerStatus.PREPARED`）。

   この手順により、メディアリソースが正常に読み込まれたことを確認します。

   >[!IMPORTANT]
   >
   >ブラウザーTVSDKが`PREPARED`状態でない場合に、以下のメソッドを呼び出そうとすると、`IllegalStateException`がスローされます。

1. `MediaPlayerItem`インターフェイスから`live`を読み取ります。

   ```js
   player.currentItem.live
   ```

