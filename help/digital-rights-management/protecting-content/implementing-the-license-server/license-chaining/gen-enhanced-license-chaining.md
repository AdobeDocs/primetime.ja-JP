---
seo-title: 拡張ライセンスチェーン
title: 拡張ライセンスチェーン
uuid: f869b4e7-4b24-4832-94a7-b7143567ab58
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 拡張ライセンスチェーン {#enhanced-license-chaining}

DRMポリシーを使用してライセンスチェーンをサポートするライセンスを生成する場合、サーバーはリーフライセンス、ルートライセンス、またはその両方を発行するかどうかを決定する必要があります。 DRMポリシーがサポートするライセンスの種類を決定する場合は、を使用するか、を呼び出して、DRMポリシーにルー `Policy.getLicenseChainType()`トライセンスが `Policy.getRootLicenseId()` あるかどうかを確認する必要があります。 Adobe Primetime DRM 2.0ライセンスチェーンを使用する場合、通常、サーバーはリーフライセンスを発行します。リーフライセンスは、ユーザーが特定のマシンのライセンスとその後のルートライセンスを最初に要求したときに発行されます。 指定したポリシーに対するリーフライセンスがコンピューターに既に存在するかどうかを確認する場合は、を呼び出す必要がありま `LicenseRequestMessage.clientHasLeafForPolicy()`す。

Adobe Primetime DRM 3.0で拡張ライセンスチェーンを使用する場合、ユーザーが最初に特定のマシンのライセンスを要求したときに、リーフとルートの両方を発行することをお勧めします。 ユーザーが既にRootライセンスを持っている場合、サーバーはリーフのみを発行する可能性があります(クライアントに3.0拡張ル `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` ートが既に存在するかどうかを確認する呼び出し)。 その後のライセンス要求では、クライアントはリーフとルートが既に存在することを示すので、サーバは新しいRootライセンスを発行する必要があります。 拡張ライセンスチェーンを使用する場合は、 `setRootKeyRetrievalInfo()` DRMポリシーのルート暗号化キーの復号化に必要な秘密鍵証明書を提供するために、を呼び出す必要があります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>ポリシーが3.0拡張ライセンスチェーンをサポートしているが、クライアントがPrimetime DRM 2.0の場合、サーバーは2.0オリジナルのチェーンライセンスを発行します。 クライアントのバージョンを確認するには、を使用しま `LicenseRequestMessage.getClientVersion()`す。

