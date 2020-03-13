---
description: Adobe Primetime DRMを使用して、Adobeによって発行されたマシンCRLを補完するCRLを作成できます。
seo-description: Adobe Primetime DRMを使用して、Adobeによって発行されたマシンCRLを補完するCRLを作成できます。
seo-title: アドビが発行したCRLを補完するCRLの生成
title: アドビが発行したCRLを補完するCRLの生成
uuid: 0cc4254d-20a0-4e05-9c5b-0b84a5c833cb
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# アドビが発行したCRLを補完するCRLの生成{#generating-crls-to-supplement-those-published-by-adobe}

Adobe Primetime DRMを使用して、Adobeによって発行されたマシンCRLを補完するCRLを作成できます。

Primetime DRM SDKはAdobe CRLを確認し、強制します。 ただし、追加のクライアントコンピューターを許可しないようにするには、CRLを作成し、CRLをPrimetime DRM SDKに渡すことで、追加のコンピューター資格情報を失効させます。 ライセンスを発行すると、SDKはAdobe CRLとCRLを確認します。

CRLを生成するには、RevocationListFactoryを参照し [てください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)。
