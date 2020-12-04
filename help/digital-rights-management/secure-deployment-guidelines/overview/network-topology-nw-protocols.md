---
description: セキュリティで保護されたネットワークアーキテクチャを設定する場合、企業ネットワーク内のAdobe PrimetimeDRMと他のシステムとのやり取りに、ネットワークプロトコルが必要です。
seo-description: セキュリティで保護されたネットワークアーキテクチャを設定する場合、企業ネットワーク内のAdobe PrimetimeDRMと他のシステムとのやり取りに、ネットワークプロトコルが必要です。
seo-title: Adobe PrimetimeDRMネットワークプロトコル
title: Adobe PrimetimeDRMネットワークプロトコル
uuid: 8954e33c-83ac-4b40-9e45-005d4954b44e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# Adobe PrimetimeDRMネットワークプロトコル{#adobe-primetime-drm-network-protocols}

セキュリティで保護されたネットワークアーキテクチャを設定する場合、企業ネットワーク内のAdobe PrimetimeDRMと他のシステムとのやり取りに、ネットワークプロトコルが必要です。

セキュリティで保護されたネットワークアーキテクチャを構成する場合、このやり取りには次のネットワークプロトコルが必要です。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_itc_33z_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロトコル </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">使用する </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR®、Adobe Primetimeの各クライアントは、HTTP経由でPrimetime DRMと通信します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS（オプション） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR、Adobe Primetimeの各クライアントは、HTTPSを使用してPrimetime DRMと通信できます。HTTPS(SSL)は、FMRMS 1.xクライアントをサポートしていない場合は不要です。 詳しくは、<a href="../../secure-deployment-guidelines/overview/network-topology-firewall-rules.md" format="dita" scope="local">着信URL </a>およびSSLの設定を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのポート{#ports-for-application-servers}

任意のネットワークポートを使用するように、Adobe PrimetimeDRMライセンスサーバーを設定できます。

Primetime DRMを実行するアプリケーションサーバーに接続するクライアントに許可するネットワーク機能に応じて、これらのポートは、内側のファイアウォールで有効または無効にする必要があります。

## SSLの設定{#configuring-ssl}

SSL(Secure Sockets Layer)は、FlashメディアRights Managementサーバー1.xクライアントのサポートが必要な場合にのみ必要です。

Adobe PrimetimeDRMキーサーバーには、クライアント認証を伴うSSLが必要です。 詳しくは、[Adobe PrimetimeDRMキーサーバーの使用](../../using-the-drm-key-server/requirements.md)を参照してください。