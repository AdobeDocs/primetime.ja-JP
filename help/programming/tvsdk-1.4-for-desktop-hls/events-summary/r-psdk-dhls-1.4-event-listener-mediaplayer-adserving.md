---
description: TVSDKは、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。
title: 広告配信/時間指定メタデータイベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# 広告配信/時間指定メタデータイベント{#ad-serving-timed-metadata-events}

TVSDKは、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。

このようなすべての関連イベントに関して通知を受けるには、次のイベントの`MediaPlayer`オブジェクトにイベントリスナーを登録します。

| イベント | 意味 |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | ID3時間指定メタデータが処理されました。 |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | 時間指定メタデータが処理され、オポチュニティが検出されませんでした。 |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | 時間指定メタデータが使用可能で、オポチュニティが検出されませんでした。 |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | 時間指定メタデータが処理され、バックグラウンドマニフェストでオポチュニティが検出されませんでした。 |