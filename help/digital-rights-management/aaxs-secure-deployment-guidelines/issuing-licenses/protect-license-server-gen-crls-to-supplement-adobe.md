---
seo-title: Adobeが発行したものを補うためのCRLの生成
title: Adobeが発行したものを補うためのCRLの生成
uuid: 4e93f6d3-5a04-44e9-9e6b-e878798b68f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Adobe{#generate-crls-to-supplement-those-published-by-adobe}が発行したものを補うCRLを生成します

Adobeアクセスを使用すると、CRLを作成して、Adobeが発行したマシンCRLを補完できます。 AdobeアクセスSDKは、AdobeCRLを確認して適用しますが、追加のコンピューター資格情報を失効させるCRLを作成することで、追加のクライアントコンピューターを無効にすることができます。 これを行うには、CRLをAdobeアクセスSDKに渡し、ライセンスを発行する際に、SDKはAdobeCRLと自分のCRLの両方を確認する必要があります。

CRLの生成について詳しくは、*AdobeアクセスAPIリファレンス*&#x200B;の`RevocationListFactory`を参照してください。
