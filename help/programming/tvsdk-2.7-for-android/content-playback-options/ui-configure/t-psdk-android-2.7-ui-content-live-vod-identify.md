---
description: メディアコンテンツがライブかビデオオンデマンドか(VOD)を知る必要がある場合があります。
seo-description: メディアコンテンツがライブかビデオオンデマンドか(VOD)を知る必要がある場合があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: d49315ee-8cec-4b79-adbd-a49c2a527424
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# コンテンツがライブかVODかの識別 {#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブかビデオオンデマンドか(VOD)を知る必要がある場合があります。

1. プレイヤーが少なくともこの状態にあることを確認し `PREPARED` てください。
1. コンテンツがラ `MediaPlayerItem` イブ()かVOD( `true`)かを指定 `false`します。

   ```java
   boolean isLive();
   ```
