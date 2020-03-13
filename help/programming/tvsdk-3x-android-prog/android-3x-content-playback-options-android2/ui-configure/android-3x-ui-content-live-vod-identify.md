---
description: メディアコンテンツがライブかビデオオンデマンドか(VOD)を知る必要がある場合があります。
seo-description: メディアコンテンツがライブかビデオオンデマンドか(VOD)を知る必要がある場合があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: e6a66104-97fb-438a-8356-e21f94058c85
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# コンテンツがライブかVODかの識別 {#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブかビデオオンデマンドか(VOD)を知る必要がある場合があります。

1. プレイヤーが少なくともこの状態にあることを確認し `PREPARED` てください。
1. コンテンツがラ `MediaPlayerItem` イブ()かVOD( `true`)かを指定 `false`します。

   ```java
   boolean isLive();
   ```
