---
title: ネットワークアクセスで使用されるAdobeプロトコル
description: ネットワークアクセスで使用されるAdobeプロトコル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# ネットワークアクセスで使用されるAdobeプロトコル {#network-protocols-used-by-adobe-access}

安全なネットワークアーキテクチャを設定する場合、Adobeアクセスと企業ネットワーク内の他のシステムとのやり取りには、次の表に示すネットワークプロトコルが必要です。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-itc-33z-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロトコル </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">用途 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTP </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR®およびAdobe Primetimeクライアントは、HTTP を介してAdobeアクセスと通信します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">HTTPS （オプション） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash Player、Adobe AIR、Adobe Primetimeの各クライアントは、Adobeアクセスとの通信に HTTPS を使用できますが、FMRMS 1.x クライアントをサポートする必要がない限り、HTTPS(SSL) は不要です。 表のメモを参照 <a href="network-topology-firewall-rules.md" format="dita" scope="local"> 受信 URL</a> および <a href="network-topology-nw-protocols.md"> SSL の設定</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
