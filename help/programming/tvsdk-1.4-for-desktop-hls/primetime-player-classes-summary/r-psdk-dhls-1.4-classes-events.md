---
description: TVSDKが様々なアクティビティに応じてメディアプレイヤーにディスパッチするイベントを記述するクラスです。
title: イベントクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---


# イベントクラス{#events-classes}

TVSDKが様々なアクティビティに応じてメディアプレイヤーにディスパッチするイベントを記述するクラスです。

パッケージ：[com.adobe.mediacore.イベント](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/package-detail.html)

| 名前 | 意味 |
|---|---|
| [AdBreakPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdBreakPlaybackEvent.html) | クラス。 広告の時間が開始または完了しました。 |
| [AdClickEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdClickEvent.html) | クラス。 ユーザーが広告をクリックしました。 |
| [AdPlaybackEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/AdPlaybackEvent.html) | クラス。 プレイヤーが広告を再生しました。 |
| [BufferEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html) | クラス。 プレイヤーがバッファリングを開始または停止しました。 |
| [CustomAdEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/advertising/CustomAdEvent.html) | クラス。 プレイヤーは、カスタム広告の読み込みステータスを表示し、エラーがある広告や読み込みに時間がかかりすぎる広告を無視できます。 |
| [DRMMetadataInfoEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html) | クラス。 新しいDRMメタデータが現在のアイテムに関連付けられています。 |
| [LoadInformationEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/LoadInformationEvent.html) | クラス。 再生中の現在のメディアストリームに対してダウンロード情報を利用できます。 |
| [MediaPlayerItemEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html) | クラス。 メディアプレイヤーアイテムが作成されました。 |
| [MediaPlayerItemLoaderEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemLoaderEvent.html) | クラス。 読み込み操作が完了しました。 `MediaPlayerItemLoader`がディスパッチして、クライアントに通知します。 |
| [MediaPlayerStatusChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html) | クラス。 メディアプレイヤーのステータスが変更されました。 |
| [MediaPlayerViewEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerViewEvent.html) | クラス。 `MediaPlayerView`がクリックされました。 |
| [PlaybackRateEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html) | クラス。 メディアプレイヤーの再生速度が変更されます。 |
| [ProfileEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html) | クラス。 ネットワークまたはマシンの状態が原因で、メディアプレイヤーの可変ビットレート切り替えアルゴリズムが別のプロファイルに切り替えられました。 |
| [SeekEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html) | クラス。 プレイヤーがシークを開始したか、シーク操作が完了しました。 |
| [SizeAvailableEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SizeAvailableEvent.html) | クラス。 ビデオサイズが使用可能です。 |
| [TimeChangeEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html) | クラス。 メディアプレイヤーのステータスが変更されました。 |
| [TimedMetadataEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html) | クラス。 時間指定メタデータがオポチュニティディテクターによって処理されます。 |
| [TimelineEvent](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html) | クラス。 メディアプレイヤーのタイムラインが変更されました。 |