---
title: ネットワークトポロジの概要
description: ネットワークトポロジの概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# 概要{#network-topology-overview}

Adobe PrimetimeDRMを正常にデプロイした後、Primetime DRM実稼働サーバーのセキュリティを維持する必要があります。

>[!NOTE]
>
>Primetime DRMは、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessでした。

*リバースプロキシ*&#x200B;を使用して、Primetime DRM Webアプリケーションの様々なURLセットを、外部ユーザーと内部ユーザーが使用できるようにします。 *リバース* プロキシは、Primetime DRMが実行されるアプリケーションサーバーへのユーザーの直接接続を許可する方法よりも高いセキュリティで保護され、この設定は、Primetime DRMを実行するアプリケーションサーバーに対するすべてのHTTP要求を実行します。ユーザーはリバースプロキシにしかアクセスできず、リバースプロキシでサポートされているURL接続のみを試行できます。

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)