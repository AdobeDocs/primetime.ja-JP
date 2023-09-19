---
description: TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークなどの QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。
title: QoS イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# QoS イベント{#qos-events}

TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークなどの QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

すべての QoS 関連イベントに関する通知を受け取るには、イベントリスナーを `MediaPlayer` オブジェクトを次のイベントに設定します。

| イベント | 意味 |
|---|---|
| BufferEvent.[BUFFERING_END](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_END) | バッファリングが完了しました。 |
| BufferEvent.[BUFFERING_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/BufferEvent.html#BUFFERING_BEGIN) | バッファリングが開始されました。 |
| SeekEvent.[SEEK_COMPLETED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_END) | シークが完了しました。 |
| SeekEvent.[SEEK_BEGIN](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_BEGIN) | シークを開始しています。 |
| SeekEvent.[SEEK_POSITION_ADJUSTED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/SeekEvent.html#SEEK_POSITION_ADJUSTED) | TVSDK は、現在の広告ポリシーの結果、シーク位置を変更しました。 |
