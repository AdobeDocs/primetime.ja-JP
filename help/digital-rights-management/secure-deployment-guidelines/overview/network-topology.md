---
seo-title: ネットワークトポロジの概要
title: ネットワークトポロジの概要
uuid: b8b072dc-8dc0-46ba-bb01-1e9b58af2681
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# 概要 {#network-topology-overview}

Adobe Primetime DRMを正常にデプロイした後は、Primetime DRM実稼働サーバーのセキュリティを維持する必要があります。

>[!NOTE]
>
>Primetime DRMは、以前はAdobe Accessと呼ばれていましたが、それ以前はFlash Accessでした。

リバースプロキシを使 *用して* 、Primetime DRM Webアプリケーションの様々なURLセットを外部ユーザーと内部ユーザーが使用できるようにします。 *リバースプロキシは* 、Primetime DRMを実行するアプリケーションサーバーにユーザーが直接接続できるよりもセキュリティが高く、この設定は、Primetime DRMを実行するアプリケーションサーバーに対するすべてのHTTP要求を実行します。 ユーザーはリバースプロキシにしかアクセスできず、リバースプロキシでサポートされているURL接続のみを試行できます。

<!--<a id="fig_8083A8C794B646CD87985EC891B60663"></a>-->

![](assets/AdobeAccess_4_SecureDeployment.png)