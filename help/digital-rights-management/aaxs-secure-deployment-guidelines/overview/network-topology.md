---
seo-title: ネットワークトポロジの概要
title: ネットワークトポロジの概要
uuid: 1558b7fa-dc0d-477c-8f1c-9c6f3718e1b0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ネットワークトポロジの概要 {#network-topology-overview}

Adobe Accessを正しく導入した後は、環境のセキュリティを維持することが重要です。 ここでは、Adobe Access実稼働サーバーのセキュリティを維持するために必要なタスクについて説明します。

リバースプ *ロキシを使用して* 、Adobe Access Webアプリケーションの様々なURLセットが外部ユーザーと内部ユーザーの両方で使用できるようにします。 この設定は、Adobe Accessが実行されているアプリケーションサーバーへのユーザーの直接接続を許可する方法よりも、より安全です。 リバースプロキシは、Adobe Accessを実行しているアプリケーションサーバーに対するすべてのHTTP要求を実行します。 ユーザーはリバースプロキシに対するネットワークアクセスのみを持ち、リバースプロキシでサポートされているURL接続のみを試行できます。

<!--<a id="fig-frx-dcg-44"></a>-->

![](assets/AdobeAccess_4_SecureDeployment_web.png)

