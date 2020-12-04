---
description: 場合によっては、メディアコンテンツがライブかVODかを知る必要があります。
seo-description: 場合によっては、メディアコンテンツがライブかVODかを知る必要があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: cd71b8d3-259a-48f8-a6ad-02b57da146a7
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# コンテンツがライブかVOD{#identify-whether-the-content-is-live-or-vod}かを識別します。

場合によっては、メディアコンテンツがライブかVODかを知る必要があります。

1. プレイヤーがPREPARED状態以上であることを確認します。
1. `MediaPlayerItem`コンテンツがライブ(true)かVOD(false)かを判定します。

   ```java
   boolean isLive();
   ```

