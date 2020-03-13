---
description: TVSDKは、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。
seo-description: TVSDKは、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。
seo-title: 広告配信/時間指定メタデータイベント
title: 広告配信/時間指定メタデータイベント
uuid: fd50a937-0c9b-4c47-acb2-1ffc0592ad54
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# 広告配信/時間指定メタデータイベント{#ad-serving-timed-metadata-events}

TVSDKは、時間指定メタデータ操作に応じて広告配信イベントをディスパッチします。

このような関連イベントの通知をすべて受け取るには、次のイベントのイベントリスナーをオ `MediaPlayer` ブジェクトに登録します。

| イベント | 意味 |
|---|---|
| TimedMetadataEvent.[TIMED_METADATA_ID3_ADDED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_ID3_ADDED) | ID3時間指定メタデータが処理されました。 |
| TimedMetadataEvent.[TIMED_METADATA_SKIPPED](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_SKIPPED) | 時間指定メタデータが処理され、オポチュニティが検出されませんでした。 |
| TimedMetadataEvent.[TIMED_METADATA_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_AVAILABLE) | 時間指定メタデータが使用可能で、オポチュニティが検出されませんでした。 |
| TimedMetadataEvent.[TIMED_METADATA_IN_BACKGROUND](https://help.stage.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_2.3/com/adobe/tvsdk/mediacore/events/TimedMetadataEvent.html#TIMED_METADATA_IN_BACKGROUND) | 時間指定メタデータが処理され、バックグラウンドマニフェストでオポチュニティが検出されませんでした。 |