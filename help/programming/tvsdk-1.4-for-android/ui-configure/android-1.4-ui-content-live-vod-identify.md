---
description: 場合によっては、メディアコンテンツがライブか VOD かを知る必要があります。
title: コンテンツがライブか VOD かを識別します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---

# コンテンツがライブか VOD かを識別します{#identify-whether-the-content-is-live-or-vod}

場合によっては、メディアコンテンツがライブか VOD かを知る必要があります。

1. プレーヤーが少なくとも PREPARED 状態であることを確認します。
1. を `MediaPlayerItem` コンテンツがライブ (true) または VOD(false) の場合。

   ```java
   boolean isLive();
   ```
