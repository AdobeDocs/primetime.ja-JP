---
seo-title: ライセンスの生成
title: ライセンスの生成
uuid: 242d5567-f609-4781-a8a6-2f3d78471344
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# ライセンスの生成{#generating-licenses}

ユーザーにリーフライセンスを発行するには、SDKは、コンテンツメタデータに含まれるCEKを復号化し、ライセンスを要求しているコンピューター用に再暗号化する必要があります。 CEKを復号化するには、サーバーがキーの復号化に必要な情報を提供する必要があります。 `ContentInfo.setKeyRetrievalInfo()`を呼び出し、`AsymmetricKeyRetrieval`オブジェクトを指定します。 メタデータに複数のポリシーが含まれる場合、サーバーは使用するポリシーを決定し、`LicenseRequestMessage.setSelectedPolicy()`を呼び出す必要があります。 次に、`LicenseRequestMessage.generateLicense()`を呼び出してライセンスを生成します。 返される`License`オブジェクトを使用して、ライセンスの有効期限や権限を変更できます。

`ContentInfo`オブジェクトでExternalKeyRetrievalオブジェクトが指定されている場合、ライセンスサーバーは、関連するCEK IDを使用して、ライセンスに挿入される適切なCEKを取得する必要があります。 外部CEKワークフローの使用方法について詳しくは、「[AdobeアクセスDRM外部CEKの概要](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)」を参照してください。
