---
seo-title: 拡張ライセンスチェーン
title: 拡張ライセンスチェーン
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# 拡張ライセンスチェーン {#enhanced-license-chaining}

Adobeアクセス3.0で拡張ライセンスチェーンを使用する場合、特定のマシンのライセンスを初めて要求する際に、リーフとルートの両方を発行することをお勧めします。 ユーザーが既にRootライセンスを持っている場合、サーバーはリーフのみを発行する可能性があります（クライアントに3.0拡張ルートが既に存在するかどうかを判断するための呼び出し）。 `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` 以降のライセンスリクエストでは、クライアントは、既にリーフとルートが存在することを示すので、サーバは新しいRootライセンスを発行する必要があります。 拡張ライセンスチェーンを使用する場合は、を呼び出して、ポリシーのルート暗号化キーの復号化に必要な秘密鍵証明書を指定する `setRootKeyRetrievalInfo()` 必要があります。

>[!NOTE]
>
>ポリシーが3.0拡張ライセンスチェーンをサポートしているが、クライアントがAdobeアクセス2.0の場合、サーバーは2.0オリジナルのチェーンライセンスを発行します。 クライアントのバージョンを確認するには、LicenseRequestMessage.getClientVersion()を使用します。

