---
description: TVSDK は、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。
title: 広告配信/時間指定メタデータイベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# 広告配信/時間指定メタデータイベント{#ad-serving-timed-metadata-events}

TVSDK は、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。

このような関連イベントに関する通知を受け取るには、イベントリスナーを `MediaPlayer` オブジェクトを次のイベントに設定します。

| イベント | 意味 |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | ID3 時間指定メタデータが処理されました。 |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | 時間指定メタデータが処理され、オポチュニティが検出されませんでした。 |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | 時間指定メタデータが使用可能で、オポチュニティが検出されませんでした。 |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | 時間指定メタデータが処理され、バックグラウンドマニフェストでオポチュニティが検出されませんでした。 |
