---
title: 同期要求の処理
description: 同期要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# 同期要求{#handling-synchronization-requests}の処理

.ライセンスで同期の要件（[同期の要件](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization)）が指定されている場合、クライアントは、ライセンスで指定されている頻度に基づいて、定期的に同期要求をサーバーに送信します。 同期メッセージを有効にするには、PlayRightでSyncFrequencyRequirementsを設定します。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバーURL:+ 「/flashaccess/sync/v4」)。 それ以外の場合、リクエストURLは「メタデータのライセンスサーバーURL」 + 「/flashaccess/sync/v3」になります。

同期メッセージは、クライアントの時刻とサーバーの時刻を同期するために使用されます。 ライセンスがコンテンツに埋め込まれていて、ライセンスサーバから取得する必要がない場合は、クライアントの時間を同期させて、クライアントがライセンスの有効期限を回避するためにクロックを変更しないようにすることが重要です。

同期メッセージを使用して、クライアント状態情報をサーバー(`getClientState()`)に通信し、ロールバック検出を行うこともできます。 [ロールバック保護](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md)を参照してください。