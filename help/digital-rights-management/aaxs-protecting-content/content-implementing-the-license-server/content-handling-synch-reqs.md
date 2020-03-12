---
seo-title: 同期要求の処理
title: 同期要求の処理
uuid: 37b2db09-4c09-4216-874b-b570a84569b6
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# 同期要求の処理{#handling-synchronization-requests}

.ライセンスで同期要件(同期の要件[](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-time-based-rules/content-time-based-rules-defining.md#requirements-for-synchronization))が指定されている場合、クライアントは、ライセンスで指定された頻度に基づいて、定期的に同期要求をサーバーに送信します。 同期メッセージを有効にするには、PlayRightでSyncFrequencyRequirementsを設定します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* クライアントとサーバの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバURL:+ &quot;/flashaccess/sync/v4&quot; それ以外の場合、要求URLは「メタデータのライセンスサーバURL」 + 「/flashaccess/sync/v3」になります。

同期メッセージは、クライアントの時刻とサーバーの時刻を同期するために使用されます。 ライセンスがコンテンツに埋め込まれていて、ライセンスサーバーから取得する必要がない場合は、クライアントの時刻を同期させることが重要です。これにより、クライアントがライセンスの有効期限切れを回避できます。

同期メッセージを使用して、クライアント状態情報をサーバ( `getClientState()`)に通信し、ロールバック検出を行うこともできます。 Rollback Protectionを参 [照してください](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-rollback-detection.md)。