---
seo-title: ライセンスの生成
title: ライセンスの生成
uuid: f91b0cc8-e0ed-4722-947b-22eb2bfba916
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# ライセンスの生成{#generating-licenses}

ユーザーにリーフライセンスを発行する場合、SDKは、コンテンツメタデータに含まれるCEKを復号化し、ライセンスを要求しているコンピューター用に再暗号化する必要があります。 CEKを復号化するには、サーバーがキーの復号化に必要な情報を提供する必要があります。 `ContentInfo.setKeyRetrievalInfo()`を呼び出し、`AsymmetricKeyRetrieval`オブジェクトを指定します。 メタデータに複数のポリシーが含まれる場合は、使用するポリシーを決定し、`LicenseRequestMessage.setSelectedPolicy()`を呼び出す必要があります。 次に、`LicenseRequestMessage.generateLicense()`を呼び出してライセンスを生成します。 返される`License`オブジェクトを使用して、ライセンスの有効期限や権限を変更できます。

`ExternalKeyRetrieval`オブジェクトが`ContentInfo`オブジェクト内で指定されている場合、ライセンスサーバーは、関連するCEK IDを使用して、ライセンスに挿入される適切なCEKを取得する必要があります。

外部CEKワークフローの使用方法の詳細については、[Adobe PrimetimeDRM外部CEKの概要](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)を参照してください。
