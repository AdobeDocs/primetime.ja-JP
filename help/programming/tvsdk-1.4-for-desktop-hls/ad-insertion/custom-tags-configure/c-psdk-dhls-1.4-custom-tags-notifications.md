---
description: MediaPlayerItem.timedMetadataプロパティを使用すると、プレイリスト/マニフェストタグまたはメディアストリーム内のID3タグから作成されたすべてのTimedMetadataオブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadataプロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。
seo-description: MediaPlayerItem.timedMetadataプロパティを使用すると、プレイリスト/マニフェストタグまたはメディアストリーム内のID3タグから作成されたすべてのTimedMetadataオブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadataプロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。
seo-title: マニフェストタグの通知
title: マニフェストタグの通知
uuid: 87bee41b-b44e-4d12-afd2-7a63023f992c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# マニフェストタグの通知{#notifications-for-manifest-tags}

MediaPlayerItem.timedMetadataプロパティを使用すると、プレイリスト/マニフェストタグまたはメディアストリーム内のID3タグから作成されたすべてのTimedMetadataオブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadataプロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。

次のイベントをリッスンして、時間指定メタデータを監視できます。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_CREATED`:オブジェクトの初期リ `TimedMetadata` ストは、を作成した後で使 `MediaPlayerItem` 用できます。 このイベントは、このような場合にアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_UPDATED`:マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される可能性があるので、TimedMetadataオブジェクトがプロパティに追加される場合が `MediaPlayerItem.timedMetadata` あります。 このイベントは、このような場合にアプリケーションに通知します。

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`:新しいオブジェクトが作成さ `TimedMetadata` れるたびに、このイベントがによって発行されま `MediaPlayer`す。 このイベントは、初期化段階で作成され `TimedMetadata` たオブジェクトに対してはディスパッチされません。

