---
seo-title: 拡張ライセンスチェーン
title: 拡張ライセンスチェーン
uuid: f869b4e7-4b24-4832-94a7-b7143567ab58
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# 拡張ライセンスチェーン {#enhanced-license-chaining}

DRMポリシーを使用してライセンスチェーンをサポートするライセンスを生成する場合、サーバーはリーフライセンス、ルートライセンス、またはその両方を発行するかどうかを決定する必要があります。 DRMポリシーがサポートするライセンスの種類を確認する場合は、を使用するか、を呼び出して、DRMポリシーにルートライセンスがあ `Policy.getLicenseChainType()``Policy.getRootLicenseId()` るかどうかを確認する必要があります。 Adobe PrimetimeDRM 2.0ライセンスチェーンでは、通常、サーバーはリーフライセンスを発行します。これは、ユーザーが特定のマシンのライセンスとルートライセンスをその後初めて要求した場合です。 指定したポリシーに対するリーフライセンスが既にコンピューターにあるかどうかを確認するには、を呼び出す必要があり `LicenseRequestMessage.clientHasLeafForPolicy()`ます。

Adobe PrimetimeDRM 3.0の拡張ライセンスチェーンでは、ユーザーが初めて特定のマシンのライセンスを要求したときにリーフとルートの両方を発行することをお勧めします。 ユーザーが既にRootライセンスを持っている場合、サーバーはリーフのみを発行する可能性があります（クライアントに3.0拡張ルートが既に存在するかどうかを判断するための呼び出し）。 `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` その後のライセンスリクエストでは、クライアントは、すでにリーフとルートが存在することを示すので、サーバは新しいRootライセンスを発行する必要があります。 拡張ライセンスチェーンを使用する場合は、を呼び出して、DRMポリシーのルート暗号化キーの復号化に必要な秘密鍵証明書を指定する `setRootKeyRetrievalInfo()` 必要があります。

>[!NOTE]
>
>ポリシーが3.0拡張ライセンスチェーンをサポートしているが、クライアントがPrimetime DRM 2.0の場合、サーバーは2.0オリジナルのチェーンライセンスを発行します。 クライアントのバージョンを確認するには、を使用し `LicenseRequestMessage.getClientVersion()`ます。

