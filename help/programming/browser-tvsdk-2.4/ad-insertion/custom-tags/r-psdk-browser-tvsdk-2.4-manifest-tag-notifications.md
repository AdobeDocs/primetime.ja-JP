---
description: MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。
title: マニフェストタグに関する通知
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# マニフェストタグ{#notifications-for-manifest-tags}の通知

MediaPlayerItem.timedMetadataプロパティは、プレイリスト/マニフェストタグまたはメディアストリームのID3タグから作成されるすべてのTimedMetadataオブジェクトへのアクセスを提供します。

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

`MediaPlayerItem.hasTimedMetadata`プロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。 `Events.TimedMetadataEvent`をリッスンすると、時間指定メタデータを監視できます。このは、新しい`TimedMetadata`オブジェクトが作成されるたびにMediaPlayerインスタンスがディスパッチします。
