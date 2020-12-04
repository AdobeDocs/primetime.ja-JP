---
description: メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。
seo-description: メディアコンテンツがライブかビデオオンデマンド(VOD)かを知る必要がある場合があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: e6a66104-97fb-438a-8356-e21f94058c85
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
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
