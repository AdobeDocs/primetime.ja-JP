---
title: Adobeが発行したものを補うためのCRLの生成
description: Adobeが発行したものを補うためのCRLの生成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Adobe{#generate-crls-to-supplement-those-published-by-adobe}が発行したものを補うCRLを生成します

Adobeアクセスを使用すると、CRLを作成して、Adobeが発行したマシンCRLを補完できます。 AdobeアクセスSDKは、AdobeCRLを確認して適用しますが、追加のコンピューター資格情報を失効させるCRLを作成することで、追加のクライアントコンピューターを無効にすることができます。 これを行うには、CRLをAdobeアクセスSDKに渡し、ライセンスを発行する際に、SDKはAdobeCRLと自分のCRLの両方を確認する必要があります。

CRLの生成について詳しくは、*AdobeアクセスAPIリファレンス*&#x200B;の`RevocationListFactory`を参照してください。
