---
description: ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバにとって最初の脅威の 1 つです。これらの脆弱性に対して、ネットワーク上のホストを強化する必要があります。
title: ネットワーク層のセキュリティ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# ネットワーク層のセキュリティ{#network-layer-security}

ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバにとって最初の脅威の 1 つです。これらの脆弱性に対して、ネットワーク上のホストを強化する必要があります。

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
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">非武装地帯 (DMZ) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Primetime DRM が内部ファイアウォールの背後にある場合に、Adobe Primetime DRM を実行するために使用されるアプリケーションサーバーと、少なくとも 2 つのレベルでセグメント化が存在する必要があります。 外部ネットワークと Web サーバーを含む DMZ を分離し、Web サーバーを内部ネットワークから分離する必要があります。 ファイアウォールを使用して、これらの分離の層を実装できます。 </p> <p>各ネットワーク層を通過するトラフィックを分類および制御して、必要最小限のデータのみを確実に許可することができます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">プライベート IP アドレス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Primetime DRM アプリケーションサーバー上の RFC 1918 プライベート IP アドレスで、Network Address Translation(NAT) を使用します。 非公開 IP アドレス (10.0.0.0/8、172.16.0.0/12および 192.168.0.0/16) を割り当てると、攻撃者がインターネットを介して NAT 内部ホストとの間でトラフィックをルーティングするのをより難しくすることができます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ファイアウォール </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ファイアウォールソリューションを選択する際に考慮すべき条件を次に示します。 </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul_wjf_lhz_n4"> 
      <li class="- topic/li " id="li_A620D0B635384590BA7804F9720D04D0">単純なパケットフィルタリングソリューションの代わりに、プロキシサーバーやステートフル検査をサポートするファイアウォールを実装します。 </li> 
      <li class="- topic/li " id="li_3E4F814A30C047539185C23F4F57C282">セキュリティパラダイムをサポートするファイアウォールを使用し、明示的に許可されたサービスを除き、すべてのサービスを拒否できます。 </li> 
      <li class="- topic/li " id="li_96160B3F14C4425397F017AF93FABE32">デュアルホームまたはマルチホームのファイアウォールソリューションを実装します。 このアーキテクチャは、最高レベルのセキュリティを提供し、不正なユーザーがファイアウォールセキュリティをバイパスするのを防ぎます。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
