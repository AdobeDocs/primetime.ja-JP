---
description: MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。
seo-description: MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。
seo-title: マニフェストタグに関する通知
title: マニフェストタグに関する通知
uuid: 50727455-b37b-4e39-8efb-a97de3164074
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# マニフェストタグ{#notifications-for-manifest-tags}の通知

MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

`MediaPlayerItem.hasTimedMetadata`プロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。 `Events.TimedMetadataEvent`をリッスンすると、時間指定メタデータを監視できます。この&lt;a0/>は、新しい`TimedMetadata`オブジェクトが作成されるたびにMediaPlayerインスタンスがディスパッチします。
