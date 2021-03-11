---
description: 場合によっては、メディアコンテンツがライブかVODかを知る必要があります。
title: コンテンツがライブかVODかの識別
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%

---


# コンテンツがライブかVOD{#identify-whether-the-content-is-live-or-vod}かを識別します。

場合によっては、メディアコンテンツがライブかVODかを知る必要があります。

1. プレイヤーがPREPARED状態以上であることを確認します。
1. `MediaPlayerItem`コンテンツがライブ(true)かVOD(false)かを判定します。

   ```java
   boolean isLive();
   ```

