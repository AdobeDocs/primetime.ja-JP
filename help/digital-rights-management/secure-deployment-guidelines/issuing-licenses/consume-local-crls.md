---
description: ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe Primetime DRM APIを使用して署名を検証します。
seo-description: ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe Primetime DRM APIを使用して署名を検証します。
seo-title: ローカルに生成されたCRLの使用
title: ローカルに生成されたCRLの使用
uuid: 2e20b8ca-8606-4c27-b585-2f020b93be32
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# ローカルに生成されたCRLの使用 {#consuming-locally-generated-crls}

ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe Primetime DRM APIを使用して署名を検証します。

次のAPIは、リストが改ざんされていないこと、およびリストが正しいLicense Serverによって署名されていることを確認します。

* RevocationList [をAPIに提供する前に](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) 、RevocationList.verifySignatureを呼び出して署名を確認 [します](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) 。

   詳しくは、RevocationListFactoryを参照して [ください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)。

* PolicyUpdateList. [verifySignatureを呼び出し](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) 、APIを提供する前に署名を確 `PolicyUpdateList` 認します。

   詳しくは、PolicyUpdateListを参照してく [ださい](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html)。

