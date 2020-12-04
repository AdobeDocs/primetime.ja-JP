---
description: MediaPlayerItem.timedMetadataプロパティを使用すると、プレイリスト/マニフェストタグまたはメディアストリーム内のID3タグから作成されたすべてのTimedMetadataオブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadataプロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。
seo-description: MediaPlayerItem.timedMetadataプロパティを使用すると、プレイリスト/マニフェストタグまたはメディアストリーム内のID3タグから作成されたすべてのTimedMetadataオブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadataプロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。
seo-title: マニフェストタグに関する通知
title: マニフェストタグに関する通知
uuid: 87bee41b-b44e-4d12-afd2-7a63023f992c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# マニフェストタグ{#notifications-for-manifest-tags}の通知

MediaPlayerItem.timedMetadataプロパティを使用すると、プレイリスト/マニフェストタグまたはメディアストリーム内のID3タグから作成されたすべてのTimedMetadataオブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadataプロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。

関連するアクティビティをアプリケーションに通知する次のイベントをリッスンすると、時間指定メタデータを監視できます。

* `MediaPlayerItemEvent.ITEM_CREATED`:オブジェクトの初期リストは、 `TimedMetadata` オブジェクトの作成後 `MediaPlayerItem` に使用できます。このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_UPDATED`:マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される場合があるので、TimedMetadataオブジェクトが `MediaPlayerItem.timedMetadata` プロパティに追加される場合があります。このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`:新しい `TimedMetadata` オブジェクトが作成されるたびに、このイベントがによってディスパッチされ `MediaPlayer`ます。初期化フェーズ中に作成された`TimedMetadata`オブジェクトに対しては、このイベントはディスパッチされません。

