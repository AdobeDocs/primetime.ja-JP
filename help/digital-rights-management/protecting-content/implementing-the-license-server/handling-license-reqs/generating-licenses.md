---
seo-title: ライセンスの生成
title: ライセンスの生成
uuid: f91b0cc8-e0ed-4722-947b-22eb2bfba916
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# ライセンスの生成{#generating-licenses}

ユーザーにリーフライセンスを発行する場合、SDKは、コンテンツメタデータに含まれるCEKを復号化し、ライセンスを要求するコンピューター用に再暗号化する必要があります。 CEKを復号化するには、サーバーがキーの復号化に必要な情報を提供する必要があります。 を呼び出し `ContentInfo.setKeyRetrievalInfo()` 、オブジェクトを指 `AsymmetricKeyRetrieval` 定します。 メタデータに複数のポリシーが含まれる場合、サーバーは、使用するポリシーと呼び出しを決定する必要がありま `LicenseRequestMessage.setSelectedPolicy()`す。 次に、を呼び出し `LicenseRequestMessage.generateLicense()` てライセンスを生成します。 返されるオ `License` ブジェクトを使用して、ライセンスの有効期限や権限を変更できます。

オブジェクト `ExternalKeyRetrieval` がオブジェクト内に指定さ `ContentInfo` れている場合、ライセンスサーバーは、ライセンスに挿入された適切なCEKを取得するために、関連付けられたCEK IDを使用する必要があります。

外部CEKワークフ [ローの使用方法について詳しくは、](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md) 「Adobe Primetime DRM外部CEKの概要」を参照してください。
