---
description: 安全なネットワークアーキテクチャを設定する場合、Adobe Primetime DRMと企業ネットワーク内の他のシステムとのやり取りには、ネットワークプロトコルが必要です。
seo-description: 安全なネットワークアーキテクチャを設定する場合、Adobe Primetime DRMと企業ネットワーク内の他のシステムとのやり取りには、ネットワークプロトコルが必要です。
seo-title: Adobe Primetime DRMネットワークプロトコル
title: Adobe Primetime DRMネットワークプロトコル
uuid: 8954e33c-83ac-4b40-9e45-005d4954b44e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Adobe Primetime DRMネットワークプロトコル {#adobe-primetime-drm-network-protocols}

安全なネットワークアーキテクチャを設定する場合、Adobe Primetime DRMと企業ネットワーク内の他のシステムとのやり取りには、ネットワークプロトコルが必要です。

セキュリティで保護されたネットワークアーキテクチャを設定する場合、このやり取りには次のネットワークプロトコルが必要です。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_itc_33z_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロトコル </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">使用 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR®およびAdobe Primetimeの各クライアントは、HTTP経由でPrimetime DRMと通信します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS（オプション） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIRおよびAdobe Primetimeクライアントは、HTTPSを使用してPrimetime DRMと通信できます。FMRMS 1.xクライアントをサポートしていない場合、HTTPS(SSL)は不要です。 詳しくは、受信URLおよびSSLの <a href="../../secure-deployment-guidelines/overview/network-topology-firewall-rules.md" format="dita" scope="local"> 設定を参 </a> 照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのポート {#ports-for-application-servers}

任意のネットワークポートを使用するようにAdobe Primetime DRMライセンスサーバーを設定できます。

Primetime DRMを実行するアプリケーションサーバーに接続するクライアントに許可するネットワーク機能に応じて、これらのポートをファイアウォール内部で有効または無効にする必要があります。

## SSLの設定 {#configuring-ssl}

Secure Sockets Layer(SSL)は、Flash Media Rights Management Server 1.xクライアントのサポートが必要な場合にのみ必要です。

Adobe Primetime DRMキーサーバーには、クライアント認証を使用するSSLが必要です。 詳しくは、Adobe Primetime DRMキー [サーバーの使用を参照してください](../../using-the-drm-key-server/requirements.md)。