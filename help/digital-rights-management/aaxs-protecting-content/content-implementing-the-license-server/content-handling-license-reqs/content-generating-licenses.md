---
seo-title: ライセンスの生成
title: ライセンスの生成
uuid: 242d5567-f609-4781-a8a6-2f3d78471344
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスの生成 {#generating-licenses}

ユーザーにリーフライセンスを発行するには、SDKは、コンテンツメタデータに含まれるCEKを復号化し、ライセンスを要求するコンピューター用に再暗号化する必要があります。 CEKを復号化するには、サーバーがキーの復号化に必要な情報を提供する必要があります。 を呼び出し `ContentInfo.setKeyRetrievalInfo()` 、オブジェクトを指 `AsymmetricKeyRetrieval` 定します。 メタデータに複数のポリシーが含まれる場合は、使用するポリシーと呼び出しをサーバーが決定する必要がありま `LicenseRequestMessage.setSelectedPolicy()`す。 次に、を呼び出し `LicenseRequestMessage.generateLicense()` てライセンスを生成します。 返されるオ `License` ブジェクトを使用して、ライセンスの有効期限や権限を変更できます。

オブジェクト内でExternalKeyRetrievalオブジェクトが指定さ `ContentInfo` れている場合、ライセンスサーバーは、関連するCEK IDを使用して、ライセンスに挿入される適切なCEKを取得する必要があります。 外部CEKワークフローの使用方法について詳しくは、「 [Adobe Access DRM外部CEKの概要」を参照してください。](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
