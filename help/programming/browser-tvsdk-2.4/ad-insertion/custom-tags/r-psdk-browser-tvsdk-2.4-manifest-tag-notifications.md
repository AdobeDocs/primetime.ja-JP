---
description: MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。
seo-description: MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。
seo-title: マニフェストタグの通知
title: マニフェストタグの通知
uuid: 50727455-b37b-4e39-8efb-a97de3164074
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# マニフェストタグの通知{#notifications-for-manifest-tags}

MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

このプロ `MediaPlayerItem.hasTimedMetadata` パティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。 時間指定メタデータを監視するには、新しいオブジェ `Events.TimedMetadataEvent`クトが作成されるたびにMediaPlayerインスタンスがディスパッチする、時間指定 `TimedMetadata` メタデータをリッスンします。
