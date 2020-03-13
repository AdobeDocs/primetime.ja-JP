---
seo-title: 同期要求の処理
title: 同期要求の処理
uuid: e2623afb-7a57-402d-a8a1-07bcf6324d41
translation-type: tm+mt
source-git-commit: eed2ed2512c2c462cd43637d83d80bf9a5c0d490

---


# 同期要求の処理 {#handle-synchronization-requests}

ライセンスで同期の要件「同期の要件 [」が指定されている場合](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) 、クライアントは、ライセンスで指定された頻度に基づいて、定期的に同期要求をサーバーに送信します。 同期メッセージを有効にするには、PlayRight `SyncFrequencyRequirements` で設定します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* クライアントとサーバの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバURL:+ &quot; [!DNL /flashaccess/sync/v4]&quot; それ以外の場合、要求URLは「メタデータのライセンスサーバURL」 + 「 [!DNL /flashaccess/sync/v3]」です

同期メッセージは、クライアントの時刻とサーバーの時刻を同期するために使用されます。 ライセンスがコンテンツに埋め込まれていて、ライセンスサーバーから取得する必要がない場合は、クライアントの時刻を同期させることが重要です。これにより、クライアントがライセンスの有効期限切れを回避できます。

同期メッセージを使用して、クライアント状態情報をサーバ( `getClientState()`)に通信し、ロールバック検出を行うこともできます。

Rollback Protectionを参 [照してください](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection)。
