---
description: TVSDK が様々なアクティビティに応じてメディアプレーヤーにディスパッチするイベントを記述するクラスです。
title: Events クラス
exl-id: a349984a-5e47-4895-a56f-ef25eb372c79
source-git-commit: 776d3d1668f063f1595bd3ecb53603171905014a
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Events クラス {#events-classes}

TVSDK が様々なアクティビティに応じてメディアプレーヤーにディスパッチするイベントを記述するクラスです。

パッケージ： [com.adobe.mediacore.events](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/package-detail.html)

| 名前 | 意味 |
|---|---|
| [AdBreakPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html) | クラス。 広告の時間が開始または完了しました。 |
| [AdClickEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html) | クラス。 ユーザーが広告をクリックした。 |
| [AdPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html) | クラス。 プレーヤーが広告を再生しました。 |
| [BufferEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html) | クラス。 プレーヤーがバッファリングを開始または停止しました。 |
| [CustomAdEvent](https://experienceleague.adobe.com/docs/primetime/programming/tvsdk-1-4-for-desktop-hls/advertising/custom-ads/r-psdk-dhls-1.4-custom-ad-events.html?lang=en) | クラス。 プレーヤーは、カスタム広告の読み込みステータスを表示し、エラーが発生した広告や読み込みに時間がかかりすぎる広告を無視できます。 |
| [DRMMetadataInfoEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html) | クラス。 新しい DRM メタデータが現在の項目に関連付けられています。 |
| [LoadInformationEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/LoadInformationEvent.html) | クラス。 再生中の現在のメディアストリームに対して、ダウンロード情報を使用できます。 |
| [MediaPlayerItemEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html) | クラス。 メディアプレーヤーアイテムが作成されました。 |
| [MediaPlayerItemLoaderEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemLoaderEvent.html) | クラス。 読み込み操作が完了しました。 ディスパッチ元 `MediaPlayerItemLoader` を使用して、クライアントに通知します。 |
| [MediaPlayerStatusChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html) | クラス。 メディアプレーヤーのステータスが変更されました。 |
| [MediaPlayerViewEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerViewEvent.html) | クラス。 この `MediaPlayerView` がクリックされました。 |
| [PlaybackRateEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html) | クラス。 メディアプレーヤーの再生速度が変わります。 |
| [ProfileEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html) | クラス。 ネットワークまたはマシンの状態が原因で、メディアプレーヤーの適応ビットレート切り替えアルゴリズムが別のプロファイルに切り替えられました。 |
| [SeekEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html) | クラス。 プレーヤーがシークを開始したか、シーク操作が完了しました。 |
| [SizeAvailableEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SizeAvailableEvent.html) | クラス。 ビデオのサイズを使用できます。 |
| [TimeChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html) | クラス。 メディアプレーヤーのステータスが変更されました。 |
| [TimedMetadataEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html) | クラス。 時間指定メタデータは、オポチュニティディテクターによって処理されます。 |
| [TimelineEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html) | クラス。 メディアプレーヤーのタイムラインが変更されました。 |
