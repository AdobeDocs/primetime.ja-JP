---
description: ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバーに対する最初の脅威の1つであり、ネットワーク上のホストをこの脆弱性に対して強化する必要があります。
title: ネットワーク層セキュリティ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# ネットワーク層セキュリティ{#network-layer-security}

ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバーに対する最初の脅威の1つであり、ネットワーク上のホストをこの脆弱性に対して強化する必要があります。

ネットワークセキュリティの脆弱性を減らす一般的な方法を次に示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_djf_lhz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">手法 </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">非武装地帯(DMZ) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Primetime DRMがファイアウォールの内側にある場合に、Adobe PrimetimeDRMを実行するために使用されるアプリケーションサーバーとの間に、少なくとも2つのレベルでセグメント化が存在する必要があります。 Webサーバーを含むDMZから外部ネットワークを分離し、Webサーバーを内部ネットワークから分離する必要があります。 これらの分離層は、ファイアウォールを使用して実装できます。 </p> <p>各ネットワーク層を通過するトラフィックを分類して制御し、必要最小限のデータのみを許可するようにできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">プライベートIPアドレス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Primetime DRMアプリケーションサーバー上のRFC 1918プライベートIPアドレスで、Network Address Translation(NAT)を使用します。 プライベートIPアドレス(10.0.0.0/8、172.16.0.0/12および192.168.0.0/16)を割り当てると、攻撃者がインターネットを介してNAT内部ホストとの間でトラフィックをルーティングするのを難しくできます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ファイアウォール </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ファイアウォールソリューションを選択する際に考慮すべき条件を以下に示します。 </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul_wjf_lhz_n4"> 
      <li class="- topic/li " id="li_A620D0B635384590BA7804F9720D04D0">単純なパケットフィルタリングソリューションではなく、プロキシサーバーやステートフルインスペクションをサポートするファイアウォールを実装します。 </li> 
      <li class="- topic/li " id="li_3E4F814A30C047539185C23F4F57C282">セキュリティの枠組みをサポートするファイアウォールを使用して、明示的に許可されたサービスを除き、すべてのサービスを拒否できます。 </li> 
      <li class="- topic/li " id="li_96160B3F14C4425397F017AF93FABE32">デュアルホームまたはマルチホームのファイアウォールソリューションを実装します。 このアーキテクチャは、最高レベルのセキュリティを提供し、権限のないユーザーがファイアウォールセキュリティを迂回するのを防ぎます。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

