---
seo-title: ネットワークトポロジの概要
title: ネットワークトポロジの概要
uuid: b8b072dc-8dc0-46ba-bb01-1e9b58af2681
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
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