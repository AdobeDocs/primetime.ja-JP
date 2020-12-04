---
description: TVSDKは、QoS(QoS)イベントをディスパッチして、バッファリングやシークなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
seo-description: TVSDKは、QoS(QoS)イベントをディスパッチして、バッファリングやシークなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
seo-title: QoSイベント
title: QoSイベント
uuid: fd657cf0-c6d4-4e9a-b212-7d09d483cae9
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# QoSイベント{#qos-events}

TVSDKは、QoS(QoS)イベントをディスパッチして、バッファリングやシークなど、QoS統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

すべてのQoS関連イベントに関して通知を受けるには、次のイベントの`MediaPlayer`オブジェクトにイベントリスナーを登録します。

| イベント | 意味 |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | バッファリングが完了しました。 |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | バッファリングが開始されました。 |
| SeekEvent.[SEEK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | シークが完了しました。 |
| SeekEvent.[SEEK_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | シークを開始しています。 |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDKは、現在の広告ポリシーの結果、シーク位置を変更しました。 |

