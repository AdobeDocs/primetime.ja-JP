---
seo-title: Adobeアクセスで使用されるネットワークプロトコル
title: Adobeアクセスで使用されるネットワークプロトコル
uuid: 4f2ee3f5-6758-4fbe-b5cd-cead1e5ccde8
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Adobeアクセスで使用されるネットワークプロトコル{#network-protocols-used-by-adobe-access}

セキュリティで保護されたネットワークアーキテクチャを設定する場合、企業ネットワーク内のAdobeアクセスと他のシステムとのやり取りには、次の表のネットワークプロトコルが必要です。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-itc-33z-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロトコル </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">使用する </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR®、Adobe Primetimeの各クライアントは、HTTP経由でAdobeアクセスと通信します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS（オプション） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR、Adobe Primetimeの各クライアントは、Adobeアクセスとの通信にHTTPSを使用できますが、FMRMS 1.xクライアントのサポートが必要な場合を除き、HTTPS(SSL)は不要です。 「<a href="network-topology-firewall-rules.md" format="dita" scope="local">受信URL </a> 」および「<a href="network-topology-nw-protocols.md"> SSLの設定</a> 」の表の注意を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>