---
title: ネットワークトポロジの概要
description: ネットワークトポロジの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# 概要 {#network-topology-overview}

Adobe Primetime DRM を正常にデプロイした後は、Primetime DRM 実稼動サーバーのセキュリティを維持する必要があります。

>[!NOTE]
>
>Primetime DRM は、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessでした。

次の項目を使用できます。 *リバースプロキシ* Primetime DRM Web アプリケーションの様々な URL セットを外部ユーザーと内部ユーザーが使用できるようにします。 *リバースプロキシ* は、Primetime DRM が実行されるアプリケーションサーバーへの直接接続をユーザーに許可するよりも安全です。この設定は、Primetime DRM を実行するアプリケーションサーバーに対するすべての HTTP リクエストを実行します。 ユーザーはリバースプロキシにのみアクセスでき、リバースプロキシでサポートされている URL 接続のみを試行できます。

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)
