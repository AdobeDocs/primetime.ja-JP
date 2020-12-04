---
description: ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe PrimetimeDRM APIを使用して署名を検証します。
seo-description: ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe PrimetimeDRM APIを使用して署名を検証します。
seo-title: ローカルに生成されたCRLの使用
title: ローカルに生成されたCRLの使用
uuid: 2e20b8ca-8606-4c27-b585-2f020b93be32
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# ローカルに生成されたCRL {#consuming-locally-generated-crls}の使用

ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe PrimetimeDRM APIを使用して署名を検証します。

次のAPIは、リストが改ざんされていないこと、およびリストが正しいLicense Serverによって署名されていることを確認します。

* [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate))を呼び出して署名を確認してから、APIに[RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html)を提供します。

   詳しくは、[RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)を参照してください。

* [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate))を呼び出して署名を確認し、`PolicyUpdateList`をAPIに提供します。

   詳しくは、[PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html)を参照してください。

