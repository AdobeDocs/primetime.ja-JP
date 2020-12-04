---
description: メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。
seo-description: メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: d49315ee-8cec-4b79-adbd-a49c2a527424
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# コンテンツがライブかVODかを識別します{#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。

1. プレイヤーが`PREPARED`状態以上であることを確認してください。
1. `MediaPlayerItem`コンテンツがライブ(`true`)かVOD(`false`)かを判断します。

   ```java
   boolean isLive();
   ```
