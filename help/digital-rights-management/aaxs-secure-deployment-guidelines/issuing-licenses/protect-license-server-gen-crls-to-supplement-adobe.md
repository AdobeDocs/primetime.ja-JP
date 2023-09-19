---
title: CRL を生成して、Adobeで公開された CRL を補完
description: CRL を生成して、Adobeで公開された CRL を補完
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# CRL を生成して、Adobeで公開された CRL を補完{#generate-crls-to-supplement-those-published-by-adobe}

Adobeアクセスを使用すると、CRL を作成して、Adobeが発行したマシン CRL を補完できます。 Adobeアクセス SDK はAdobeCRL を確認して適用しますが、追加のクライアントコンピューターの資格情報を取り消す CRL を作成することで、追加のクライアントマシンを許可しなくすることができます。 これをおこなうには、CRL をAdobeアクセス SDK に渡し、ライセンスを発行する際に、SDK はAdobeCRL と独自の CRL の両方を確認する必要があります。

CRL の生成について詳しくは、 `RevocationListFactory` in *Adobeアクセス API リファレンス*.
