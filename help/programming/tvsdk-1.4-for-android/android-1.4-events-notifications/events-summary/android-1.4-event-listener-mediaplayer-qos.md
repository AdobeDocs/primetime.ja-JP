---
description: TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークなどの QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
title: QoS イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# QoS イベント{#qos-events}

TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークなどの QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

すべての QoS 関連イベントに関する通知を受け取るには、 `MediaPlayer.QOSEventListener` 次のコールバックが含まれます。

| イベント | 意味 |
|---|---|
| [onBufferComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferComplete()) | バッファリングが完了しました。 |
| [onBufferStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onBufferStart()) | バッファリングが開始されました。 |
| [onLoadInfo](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onLoadInfo(com.adobe.mediacore.qos.LoadInfo))(loadInfo) | フラグメントが正常にダウンロードされました。 |
| [onOperationFailed](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html)(MediaPlayerNotification. [警告](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.Warning.html) 警告 ) | 回復可能なエラーが発生しました。 |
| [onSeekComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekComplete(long))（長い adjustedTime） | シークが完了しました。 |
| [onSeekStart](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html#onSeekStart()) | シークを開始しています。 |
