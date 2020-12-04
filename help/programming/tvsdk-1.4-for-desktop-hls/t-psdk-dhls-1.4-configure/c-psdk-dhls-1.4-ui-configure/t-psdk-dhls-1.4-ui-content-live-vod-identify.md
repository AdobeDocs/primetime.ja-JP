---
description: 場合によっては、メディアコンテンツがライブかVODかを知る必要があります。
seo-description: 場合によっては、メディアコンテンツがライブかVODかを知る必要があります。
seo-title: コンテンツがライブかVODかの識別
title: コンテンツがライブかVODかの識別
uuid: 4d514c46-a1d0-4721-a423-92108126e37e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# コンテンツがライブかVOD{#identify-whether-the-content-is-live-or-vod}かを識別します。

場合によっては、メディアコンテンツがライブかVODかを知る必要があります。

1. プレイヤーがINITIALIZEDステータス以上であることを確認してください。
1. `MediaPlayerItem`コンテンツがライブ(true)かVOD(false)かを判定します。

   ```
   function get isLive():Boolean;
   ```

