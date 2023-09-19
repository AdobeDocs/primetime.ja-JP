---
description: メディアコンテンツがライブかビデオオンデマンド (VOD) かを知る必要が生じる場合があります。
title: コンテンツがライブか VOD かを識別します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---

# コンテンツがライブか VOD かを識別します {#identify-whether-the-content-is-live-or-vod}

メディアコンテンツがライブかビデオオンデマンド (VOD) かを知る必要が生じる場合があります。

1. プレーヤーが少なくとも `PREPARED` 状態。
1. を `MediaPlayerItem` コンテンツはライブです ( `true`) または VOD ( `false`) をクリックします。

   ```java
   boolean isLive();
   ```
