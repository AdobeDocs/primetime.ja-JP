---
title: ネットワーク層のセキュリティ
description: ネットワーク層のセキュリティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# ネットワーク層のセキュリティ{#network-layer-security}

ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバーにとって、最初の脅威の 1 つです。 この節では、これらの脆弱性に対してネットワーク上のホストを強化するプロセスについて説明します。 これは、ネットワークのセグメント化、TCP/IP(Transmission Control Protocol/Internet Protocol) スタックの堅牢化、およびホスト保護のためのファイアウォールの使用に対応しています。

次の表は、ネットワークセキュリティの脆弱性を減らす一般的な方法を示しています。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-djf-lhz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">手法 </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">非武装地帯 (DMZ) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">セグメント化は、内側のファイアウォールの後ろに配置されたAdobeアクセスを実行するために使用されるアプリケーションサーバーと少なくとも 2 つのレベルに存在する必要があります。 Web サーバーを含む DMZ から外部ネットワークを分離します。その後、外部ネットワークを内部ネットワークから分離する必要があります。 ファイアウォールを使用して、分離の層を実装します。 各ネットワーク層を通過するトラフィックを分類および制御して、必要最小限のデータのみが許可されるようにします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">プライベート IP アドレス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Adobeアクセスアプリケーションサーバー上の RFC 1918 プライベート IP アドレスで、Network Address Translation（NAT；ネットワークアドレス変換）を使用します。 非公開 IP アドレス (10.0.0.0/8、172.16.0.0/12、192.168.0.0/16) を割り当てて、攻撃者がインターネットを介して NAT 内部ホストとの間でトラフィックのルーティングをより困難にします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ファイアウォール </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">次の条件を使用して、ファイアウォールソリューションを選択します。 </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul-wjf-lhz-n4"> 
      <li class="- topic/li " id="li-8031632160F44037B092988183139202"> <p class="- topic/p ">単純なパケットフィルタリングソリューションの代わりに、プロキシサーバーやステートフル検査をサポートするファイアウォールを実装します。 </p> </li> 
      <li class="- topic/li " id="li-B65CBB92113E4503B79EB194C34FCA50"> <p class="- topic/p ">セキュリティパラダイムをサポートするファイアウォールを使用し、明示的に許可されたサービスを除くすべてのサービスを拒否できます。 </p> </li> 
      <li class="- topic/li " id="li-5CE4C7B65D84410DB4BE966FD8922993"> <p class="- topic/p ">デュアルホームまたはマルチホームのファイアウォールソリューションを実装します。 このアーキテクチャは、最高レベルのセキュリティを提供し、不正なユーザーがファイアウォールセキュリティをバイパスするのを防ぐのに役立ちます。 </p> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
