---
description: MediaPlayerItem.timedMetadata プロパティを使用すると、プレイリスト/マニフェストタグ、またはメディアストリームの ID3 タグから作成されるすべての TimedMetadata オブジェクトにアクセスできます。
title: マニフェストタグに関する通知
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# マニフェストタグに関する通知{#notifications-for-manifest-tags}

MediaPlayerItem.timedMetadata プロパティを使用すると、プレイリスト/マニフェストタグ、またはメディアストリームの ID3 タグから作成されるすべての TimedMetadata オブジェクトにアクセスできます。

<!--<a id="section_9A22F6F1EA1F4F0C9E0C7687D12AA4AA"></a>-->

The `MediaPlayerItem.hasTimedMetadata` プロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。 時間指定メタデータを監視するには、 `Events.TimedMetadataEvent`：新しい `TimedMetadata` オブジェクトが作成されます。
