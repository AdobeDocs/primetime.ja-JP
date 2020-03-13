---
seo-title: Adobe Accessで使用されるネットワークプロトコル
title: Adobe Accessで使用されるネットワークプロトコル
uuid: 4f2ee3f5-6758-4fbe-b5cd-cead1e5ccde8
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Adobe Accessで使用されるネットワークプロトコル {#network-protocols-used-by-adobe-access}

安全なネットワークアーキテクチャを設定する場合、Adobe Accessと企業ネットワーク内の他のシステムとのやり取りには、次の表に示すネットワークプロトコルが必要です。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-itc-33z-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロトコル </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">使用 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR®およびAdobe Primetimeの各クライアントは、HTTP経由でAdobe Accessと通信します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS（オプション） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIRおよびAdobe Primetimeの各クライアントは、Adobe Accessとの通信にHTTPSを使用できますが、FMRMS 1.xクライアントのサポートが必要な場合を除き、HTTPS(SSL)は不要です。 受信URLとSSLの設定の表の注 <a href="network-topology-firewall-rules.md" format="dita" scope="local"> 意を参照し</a> てください <a href="network-topology-nw-protocols.md"></a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>