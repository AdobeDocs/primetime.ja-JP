---
title: ライセンスの生成
description: ライセンスの生成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# ライセンスの生成{#generating-licenses}

ユーザーにリーフライセンスを発行する場合、SDKは、コンテンツメタデータに含まれるCEKを復号化し、ライセンスを要求しているコンピューター用に再暗号化する必要があります。 CEKを復号化するには、サーバーがキーの復号化に必要な情報を提供する必要があります。 `ContentInfo.setKeyRetrievalInfo()`を呼び出し、`AsymmetricKeyRetrieval`オブジェクトを指定します。 メタデータに複数のポリシーが含まれる場合は、使用するポリシーを決定し、`LicenseRequestMessage.setSelectedPolicy()`を呼び出す必要があります。 次に、`LicenseRequestMessage.generateLicense()`を呼び出してライセンスを生成します。 返される`License`オブジェクトを使用して、ライセンスの有効期限や権限を変更できます。

`ExternalKeyRetrieval`オブジェクトが`ContentInfo`オブジェクト内で指定されている場合、ライセンスサーバーは、関連するCEK IDを使用して、ライセンスに挿入される適切なCEKを取得する必要があります。

外部CEKワークフローの使用方法の詳細については、[Adobe PrimetimeDRM外部CEKの概要](../../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)を参照してください。
