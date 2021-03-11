---
title: 拡張ライセンスチェーン
description: 拡張ライセンスチェーン
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# 拡張ライセンスチェーン{#enhanced-license-chaining}

Adobeアクセス3.0で拡張ライセンスチェーンを使用する場合、特定のマシンのライセンスを初めて要求する際に、リーフとルートの両方を発行することをお勧めします。 ユーザーが既にRootライセンスを持っている場合、サーバーはリーフのみを発行する可能性があります（`LicenseRequestMessage.clientHasEnhancedRootForPolicy()`を呼び出して、クライアントに3.0拡張ルートが既に存在するかどうかを判断します）。 以降のライセンスリクエストでは、クライアントは、既にリーフとルートが存在することを示すので、サーバは新しいRootライセンスを発行する必要があります。 拡張ライセンスチェーンを使用する場合は、`setRootKeyRetrievalInfo()`を呼び出して、ポリシーのルート暗号化キーの復号化に必要な資格情報を指定する必要があります。

>[!NOTE]
>
>ポリシーが3.0拡張ライセンスチェーンをサポートしているが、クライアントがAdobeアクセス2.0の場合、サーバーは2.0オリジナルのチェーンライセンスを発行します。 クライアントのバージョンを確認するには、LicenseRequestMessage.getClientVersion()を使用します。

