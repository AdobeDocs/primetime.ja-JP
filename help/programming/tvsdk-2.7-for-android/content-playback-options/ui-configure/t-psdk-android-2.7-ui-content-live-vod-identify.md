---
description: メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。
title: コンテンツがライブかVODかの識別
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# コンテンツがライブかVODかを識別します{#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。

1. プレイヤーが`PREPARED`状態以上であることを確認してください。
1. `MediaPlayerItem`コンテンツがライブ(`true`)かVOD(`false`)かを判断します。

   ```java
   boolean isLive();
   ```
