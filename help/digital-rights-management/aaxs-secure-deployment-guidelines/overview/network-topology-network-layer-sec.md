---
title: ネットワーク層セキュリティ
description: ネットワーク層セキュリティ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# ネットワーク層セキュリティ{#network-layer-security}

ネットワークセキュリティの脆弱性は、インターネットまたはイントラネットに接続するアプリケーションサーバーにとって、最も脅威の1つです。 この節では、これらの脆弱性に対してネットワーク上のホストを堅牢化するプロセスについて説明します。 ネットワークのセグメント化、TCP/IP(Transmission Control Protocol/Internet Protocol)スタックの堅牢化、およびホスト保護のためのファイアウォールの使用について説明します。

次の表に、ネットワークセキュリティの脆弱性を減らす一般的な方法を示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-djf-lhz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">手法 </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">非武装地帯(DMZ) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ファイアウォールの内側に配置されたAdobeアクセスを実行するアプリケーションサーバーに対して、少なくとも2つのレベルでセグメント化が必要です。 Webサーバーを含むDMZから外部ネットワークを分離します。その後、外部ネットワークを内部ネットワークから分離する必要があります。 ファイアウォールを使用して、分離した層を実装します。 必要最小限のデータのみが許可されるように、各ネットワーク層を通過するトラフィックを分類して制御します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">プライベートIPアドレス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Adobeアクセスアプリケーションサーバーで、RFC 1918プライベートIPアドレスにNetwork Address Translation(NAT)を使用します。 プライベートIPアドレス(10.0.0.0/8、172.16.0.0/12、192.168.0.0/16)を割り当てると、攻撃者がインターネット経由でNAT内部ホストとの間でトラフィックをルーティングするのをより困難にします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ファイアウォール </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">次の条件を使用して、ファイアウォールソリューションを選択します。 </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul-wjf-lhz-n4"> 
      <li class="- topic/li " id="li-8031632160F44037B092988183139202"> <p class="- topic/p ">単純なパケットフィルタリングソリューションではなく、プロキシサーバーやステートフルインスペクションをサポートするファイアウォールを実装します。 </p> </li> 
      <li class="- topic/li " id="li-B65CBB92113E4503B79EB194C34FCA50"> <p class="- topic/p ">セキュリティの枠組みをサポートするファイアウォールを使用して、明示的に許可されたサービス以外のすべてのサービスを拒否できます。 </p> </li> 
      <li class="- topic/li " id="li-5CE4C7B65D84410DB4BE966FD8922993"> <p class="- topic/p ">デュアルホームまたはマルチホームのファイアウォールソリューションを実装します。 このアーキテクチャは、最高レベルのセキュリティを提供し、権限のないユーザーがファイアウォールセキュリティを迂回するのを防ぐのに役立ちます。 </p> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

