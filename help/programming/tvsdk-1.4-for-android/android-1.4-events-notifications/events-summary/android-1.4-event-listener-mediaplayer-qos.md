---
description: TVSDKは、サービス品質(QoS)イベントをディスパッチして、バッファリングやシークなどのQoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
seo-description: TVSDKは、サービス品質(QoS)イベントをディスパッチして、バッファリングやシークなどのQoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
seo-title: QoSイベント
title: QoSイベント
uuid: 27f60cd3-d3fc-4ea3-81df-96d0fe9f7068
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# QoSイベント{#qos-events}

TVSDKは、サービス品質(QoS)イベントをディスパッチして、バッファリングやシークなどのQoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

QoS関連のすべてのイベントに関する通知を受け取るには、以下のコールバックを含む実装 `MediaPlayer.QOSEventListener` を登録してください。

| イベント | 意味 |
|---|---|
| [onBufferComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferComplete()) | バッファリングが完了しました。 |
| [onBufferStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferStart()) | バッファリングが開始されました。 |
| [onLoadInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onLoadInfo(com.adobe.mediacore.qos.LoadInfo))(loadInfo) | フラグメントが正常にダウンロードされました。 |
| [onOperationFailed](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html)(MediaPlayerNotification. [警告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) ) | 回復可能なエラーが発生しました。 |
| [onSeekComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekComplete(long))(long adjustedTime) | シークが完了しました。 |
| [onSeekStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekStart()) | シークを開始しています。 |