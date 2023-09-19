---
title: ライセンスの生成
description: ライセンスの生成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# ライセンスの生成 {#generating-licenses}

ユーザーにリーフライセンスを発行するには、SDK は、コンテンツメタデータに含まれる CEK を復号化し、ライセンスを要求するマシン用に再暗号化する必要があります。 CEK を復号化するには、サーバーがキーを復号化するために必要な情報を提供する必要があります。 通話 `ContentInfo.setKeyRetrievalInfo()` と、 `AsymmetricKeyRetrieval` オブジェクト。 メタデータに複数のポリシーが含まれる場合、サーバーは、使用するポリシーを決定し、を呼び出す必要があります `LicenseRequestMessage.setSelectedPolicy()`. 次に、を呼び出します。 `LicenseRequestMessage.generateLicense()` をクリックしてライセンスを生成します。 の使用 `License` 返されるオブジェクトに対しては、ライセンスの有効期限または権限を変更できます。

ExternalKeyRetrieval オブジェクトが `ContentInfo` オブジェクトの場合、ライセンスサーバーは、関連する CEK ID を使用して、ライセンスに挿入される適切な CEK を取得する必要があります。 外部 CEK ワークフローの使用方法について詳しくは、 [Adobeアクセス DRM 外部 CEK の概要](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)
