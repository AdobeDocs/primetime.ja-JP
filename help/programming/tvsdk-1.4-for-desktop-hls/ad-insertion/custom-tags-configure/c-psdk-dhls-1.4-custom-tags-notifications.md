---
description: MediaPlayerItem.timedMetadata プロパティを使用すると、プレイリスト/マニフェストタグ、またはメディアストリーム内の ID3 タグから作成されるすべての TimedMetadata オブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadata プロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。
title: マニフェストタグに関する通知
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# マニフェストタグに関する通知{#notifications-for-manifest-tags}

MediaPlayerItem.timedMetadata プロパティを使用すると、プレイリスト/マニフェストタグ、またはメディアストリーム内の ID3 タグから作成されるすべての TimedMetadata オブジェクトにアクセスできます。 MediaPlayerItem.hasTimedMetadata プロパティは、サブスクライブされたカスタムタグが現在のメディアに存在するかどうかを示します。

時間指定メタデータを監視するには、次のイベントをリッスンします。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_CREATED`：の最初のリスト `TimedMetadata` オブジェクトは、 `MediaPlayerItem` が作成されました。 このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `MediaPlayerItemEvent.ITEM_UPDATED`：マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される可能性があるので、追加の TimedMetadata オブジェクトが `MediaPlayerItem.timedMetadata` プロパティ。 このイベントは、このような状況が発生した場合にアプリケーションに通知します。

* `TimedMetadataEvent.TIMED_METADATA_AVAILABLE`：新しい `TimedMetadata` オブジェクトが作成された場合、このイベントは `MediaPlayer`. このイベントは、 `TimedMetadata` オブジェクトが初期化フェーズ中に作成されました。
