---
description: メディアコンテンツがライブかVODかを知る必要がある場合があります。
title: コンテンツがライブかVODかの識別
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---


# コンテンツがライブかVOD{#identify-whether-the-content-is-live-or-vod}かを識別します。

メディアコンテンツがライブかVODかを知る必要がある場合があります。

1. ブラウザーTVSDKが`AdobePSDK.PSDKEventType.STATUS_CHANGED`イベントと`event.status`のトリガーを待ちます。`AdobePSDK.MediaPlayerStatus.PREPARED`は

   この手順により、メディアリソースが正常に読み込まれたことを確認します。

   >[!IMPORTANT]
   >
   >ブラウザーTVSDKが`PREPARED`状態でない場合に、以下のメソッドを呼び出そうとすると、`IllegalStateException`がスローされます。

1. `MediaPlayerItem`インターフェイスから`live`を読み取ります。

   ```js
   player.currentItem.live
   ```

