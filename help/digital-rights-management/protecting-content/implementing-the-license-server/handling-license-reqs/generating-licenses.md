---
title: ライセンスの生成
description: ライセンスの生成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# ライセンスの生成{#generating-licenses}

ユーザーにリーフライセンスを発行する場合、SDK は、コンテンツメタデータに含まれる CEK を復号化し、ライセンスをリクエストするマシン用に再暗号化する必要があります。 CEK を復号化するには、サーバーがキーを復号化するために必要な情報を提供する必要があります。 通話 `ContentInfo.setKeyRetrievalInfo()` と、 `AsymmetricKeyRetrieval` オブジェクト。 メタデータに複数のポリシーが含まれる場合、サーバーは、使用するポリシーを決定し、を呼び出す必要があります `LicenseRequestMessage.setSelectedPolicy()`. 次に、を呼び出します。 `LicenseRequestMessage.generateLicense()` をクリックしてライセンスを生成します。 の使用 `License` 返されるオブジェクトに対しては、ライセンスの有効期限または権限を変更できます。

次の場合、 `ExternalKeyRetrieval` オブジェクトが `ContentInfo` オブジェクトの場合、ライセンスサーバーは関連する CEK ID を使用して、ライセンスに挿入された適切な CEK を取得する必要があります。

詳しくは、 [Adobe Primetime DRM 外部 CEK の概要](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md) 外部 CEK ワークフローの使用方法の詳細については、を参照してください。
