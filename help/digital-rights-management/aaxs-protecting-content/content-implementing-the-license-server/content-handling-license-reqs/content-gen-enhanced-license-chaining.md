---
seo-title: 拡張ライセンスチェーン
title: 拡張ライセンスチェーン
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: da8736769f7b47318dbd955aa854f83ae64d6d7b

---


# 拡張ライセンスチェーン {#enhanced-license-chaining}

Adobe Access 3.0で拡張ライセンスチェーンを使用する場合は、ユーザーが最初に特定のマシンのライセンスを要求したときに、リーフとルートの両方を発行することをお勧めします。 ユーザーが既にRootライセンスを持っている場合、サーバーはリーフのみを発行する可能性があります(クライアントに3.0拡張ル `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` ートが既に存在するかどうかを確認する呼び出し)。 その後のライセンス要求では、クライアントはリーフとルートが既に存在することを示すので、サーバは新しいRootライセンスを発行する必要があります。 拡張ライセンスチェーンを使用する場合は、 `setRootKeyRetrievalInfo()` を呼び出して、ポリシーのルート暗号化キーの復号化に必要な資格情報を提供する必要があります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>ポリシーが3.0拡張ライセンスチェーンをサポートしているが、クライアントがAdobe Access 2.0の場合、サーバーは2.0の元のチェーンライセンスを発行します。 クライアントのバージョンを確認するには、LicenseRequestMessage.getClientVersion()を使用します。

