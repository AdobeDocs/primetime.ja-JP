---
title: 拡張ライセンスチェーン
description: 拡張ライセンスチェーン
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# 拡張ライセンスチェーン{#enhanced-license-chaining}

DRMポリシーを使用してライセンスチェーンをサポートするライセンスを生成する場合、サーバーはリーフライセンス、ルートライセンス、またはその両方を発行するかどうかを決定する必要があります。 DRMポリシーがサポートするライセンスの種類を確認するには、`Policy.getLicenseChainType()`を使用するか、`Policy.getRootLicenseId()`を呼び出してDRMポリシーにルートライセンスがあるかどうかを確認する必要があります。 Adobe PrimetimeDRM 2.0ライセンスチェーンでは、通常、サーバーはリーフライセンスを発行します。これは、ユーザーが特定のマシンのライセンスとルートライセンスをその後初めて要求した場合です。 指定したポリシーに対するリーフライセンスが既にマシンに存在するかどうかを判断するには、`LicenseRequestMessage.clientHasLeafForPolicy()`を呼び出す必要があります。

Adobe PrimetimeDRM 3.0の拡張ライセンスチェーンでは、ユーザーが初めて特定のマシンのライセンスを要求したときにリーフとルートの両方を発行することをお勧めします。 ユーザーが既にRootライセンスを持っている場合、サーバーはリーフのみを発行する可能性があります（`LicenseRequestMessage.clientHasEnhancedRootForPolicy()`を呼び出して、クライアントに3.0拡張ルートが既に存在するかどうかを判断します）。 その後のライセンスリクエストでは、クライアントはリーフとルートが既に存在することを示すので、サーバは新しいRootライセンスを発行する必要があります。 拡張ライセンスチェーンを使用する場合は、`setRootKeyRetrievalInfo()`を呼び出して、DRMポリシーのルート暗号化キーの復号化に必要な秘密鍵証明書を提供する必要があります。

>[!NOTE]
>
>ポリシーが3.0拡張ライセンスチェーンをサポートしているが、クライアントがPrimetime DRM 2.0の場合、サーバーは2.0オリジナルのチェーンライセンスを発行します。 クライアントのバージョンを確認するには、`LicenseRequestMessage.getClientVersion()`を使用します。

