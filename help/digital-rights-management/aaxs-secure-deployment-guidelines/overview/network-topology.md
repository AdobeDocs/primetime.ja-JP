---
title: ネットワークトポロジの概要
description: ネットワークトポロジの概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# ネットワークトポロジの概要{#network-topology-overview}

Adobeアクセスを正しく展開した後は、環境のセキュリティを維持することが重要です。 ここでは、Adobeアクセス実稼働サーバーのセキュリティを維持するために必要なタスクについて説明します。

*リバースプロキシ*&#x200B;を使用して、AdobeアクセスWebアプリケーションの異なるURLセットを、外部ユーザーと内部ユーザーの両方から利用できるようにします。 この設定は、Adobeアクセスが実行されているアプリケーションサーバーへのユーザーの直接接続を許可する方法よりも、高いセキュリティで保護されます。 リバースプロキシは、Adobeアクセスを実行しているアプリケーションサーバーに対するすべてのHTTP要求を実行します。 ユーザーはリバースプロキシに対するネットワークアクセスのみを持ち、リバースプロキシでサポートされているURL接続のみを試行できます。

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)

