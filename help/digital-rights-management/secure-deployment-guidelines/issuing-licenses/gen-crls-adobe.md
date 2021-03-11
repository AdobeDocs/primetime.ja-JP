---
description: Adobe PrimetimeDRMを使用して、Adobeが発行するマシンCRLを補完するCRLを作成できます。
title: Adobeが発行したCRLを補うCRLの生成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Adobe{#generating-crls-to-supplement-those-published-by-adobe}が発行したCRLを補うCRLの生成

Adobe PrimetimeDRMを使用して、Adobeが発行するマシンCRLを補完するCRLを作成できます。

Primetime DRM SDKがチェックし、AdobeCRLを強制します。 ただし、追加のクライアントコンピューターを許可しない場合は、CRLをPrimetime DRM SDKに渡すことで、追加のコンピューターの秘密鍵証明書を失効させるCRLを作成します。 ライセンスを発行すると、SDKはAdobeCRLとCRLを確認します。

CRLを生成するには、[RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)を参照してください。
