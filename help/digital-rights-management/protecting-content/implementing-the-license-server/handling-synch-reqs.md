---
seo-title: 同期要求の処理
title: 同期要求の処理
uuid: e2623afb-7a57-402d-a8a1-07bcf6324d41
translation-type: tm+mt
source-git-commit: eed2ed2512c2c462cd43637d83d80bf9a5c0d490
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# 同期要求を処理{#handle-synchronization-requests}

ライセンスが同期の要件[同期の要件を指定した場合、](../../protecting-content/introduction/usage-rules/authentication/synchronization.md)クライアントは、ライセンスで指定された頻度に基づいて、定期的に同期要求をサーバに送信します。 同期メッセージを有効にするには、PlayRightに`SyncFrequencyRequirements`を設定します。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバーURL:+ &quot; [!DNL /flashaccess/sync/v4]&quot;。 それ以外の場合、要求URLは「メタデータのライセンスサーバーURL」 + 「 [!DNL /flashaccess/sync/v3]」になります。

同期メッセージは、クライアントの時刻とサーバーの時刻を同期するために使用されます。 ライセンスがコンテンツに埋め込まれていて、ライセンスサーバから取得する必要がない場合は、クライアントの時間を同期させて、クライアントがライセンスの有効期限を回避するためにクロックを変更しないようにすることが重要です。

同期メッセージを使用して、クライアント状態情報をサーバー(`getClientState()`)に通信し、ロールバック検出を行うこともできます。

[ロールバック保護](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection)を参照してください。
