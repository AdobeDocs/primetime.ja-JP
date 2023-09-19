---
title: 同期リクエストの処理
description: 同期リクエストの処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# 同期リクエストの処理 {#handle-synchronization-requests}

ライセンスで同期要件が指定されている場合  [同期の要件、](../../protecting-content/introduction/usage-rules/authentication/synchronization.md) クライアントは、ライセンスで指定された頻度に基づいて、サーバに対して定期的に同期要求を送信します。 同期メッセージを有効にするには、 `SyncFrequencyRequirements` PlayRight の。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.sync.SynchronizationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「メタデータのライセンスサーバー URL: + 」です。 [!DNL /flashaccess/sync/v4]&quot;. それ以外の場合、リクエスト URL は「メタデータのライセンスサーバー URL」 + 「 」です。 [!DNL /flashaccess/sync/v3]&quot;

同期メッセージは、クライアントの時刻とサーバーの時刻を同期するために使用されます。 ライセンスがコンテンツに埋め込まれ、ライセンスサーバから取得する必要がない場合は、クライアントがライセンスの有効期限を回避するためにクライアントのクロックを変更しないように、クライアントの時刻を同期することが重要です。

同期メッセージを使用して、クライアントの状態情報をサーバーに伝えることもできます ( `getClientState()`) を使用して、ロールバック検出を行います。

詳しくは、 [ロールバック保護](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#rollback-detection).
