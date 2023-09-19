---
description: 安全なネットワークアーキテクチャを設定する場合、Adobe Primetime DRM とエンタープライズネットワーク内の他のシステムとの間のやり取りには、ネットワークプロトコルが必要です。
title: Adobe Primetime DRM ネットワークプロトコル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Adobe Primetime DRM ネットワークプロトコル {#adobe-primetime-drm-network-protocols}

安全なネットワークアーキテクチャを設定する場合、Adobe Primetime DRM とエンタープライズネットワーク内の他のシステムとの間のやり取りには、ネットワークプロトコルが必要です。

セキュアなネットワークアーキテクチャを設定する場合、この操作には次のネットワークプロトコルが必要です。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_itc_33z_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロトコル </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">用途 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR®およびAdobe Primetimeのクライアントは、HTTP 経由で Primetime DRM と通信します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS （オプション） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIRおよびAdobe Primetimeのクライアントは、HTTPS を使用して Primetime DRM と通信できます。FMRMS 1.x クライアントをサポートしていない場合、HTTPS(SSL) は不要です。 詳しくは、 <a href="../../secure-deployment-guidelines/overview/network-topology-firewall-rules.md" format="dita" scope="local"> 受信 URL </a> と SSL の設定を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのポート {#ports-for-application-servers}

任意のネットワークポートを使用するようにAdobe Primetime DRM ライセンスサーバーを設定できます。

Primetime DRM を実行するアプリケーションサーバーに接続するクライアントに許可するネットワーク機能に応じて、これらのポートを内側のファイアウォールで有効または無効にする必要があります。

## SSL の設定 {#configuring-ssl}

Secure Sockets Layer(SSL) は、FlashMediaRights Managementサーバー 1.x クライアントのサポートが必要な場合にのみ必要です。

Adobe Primetime DRM キーサーバーを使用するには、クライアント認証を使用する SSL が必要です。 詳しくは、 [Adobe Primetime DRM キーサーバーの使用](../../using-the-drm-key-server/requirements.md).
