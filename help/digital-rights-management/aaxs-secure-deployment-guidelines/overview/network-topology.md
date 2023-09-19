---
title: ネットワークトポロジの概要
description: ネットワークトポロジの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---

# ネットワークトポロジの概要 {#network-topology-overview}

Adobeアクセスを正常にデプロイした後は、環境のセキュリティを維持することが重要です。 このセクションでは、実稼動サーバーのセキュリティを維持するために必要なAdobeについて説明します。

の使用 *リバースプロキシ* を使用して、外部ユーザーと内部ユーザーの両方が、Adobeアクセス Web アプリケーションの様々な URL セットを使用できるようにします。 この設定は、ユーザーがアプリケーションアクセスを実行しているアプリケーションサーバーへの直接接続を許可するAdobeよりも安全です。 リバースプロキシは、Adobeアクセスを実行しているアプリケーションサーバーに対するすべての HTTP リクエストを実行します。 ユーザーはリバースプロキシに対するネットワークアクセスのみを持ち、リバースプロキシでサポートされる URL 接続のみを試行できます。

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)
