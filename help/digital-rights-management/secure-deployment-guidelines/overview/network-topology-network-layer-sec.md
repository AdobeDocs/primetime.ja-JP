---
description: ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバに対する最初の脅威の1つであり、これらの脆弱性に対してネットワーク上のホストを強化する必要があります。
seo-description: ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバに対する最初の脅威の1つであり、これらの脆弱性に対してネットワーク上のホストを強化する必要があります。
seo-title: ネットワーク層セキュリティ
title: ネットワーク層セキュリティ
uuid: c750c595-a784-47ce-be0b-17b8d60c5753
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ネットワーク層セキュリティ{#network-layer-security}

ネットワークセキュリティの脆弱性は、インターネットやイントラネットに接続するアプリケーションサーバに対する最初の脅威の1つであり、これらの脆弱性に対してネットワーク上のホストを強化する必要があります。

ネットワークセキュリティの脆弱性を減らす一般的な方法を次に示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_djf_lhz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">技術 </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">非武装地帯(DMZ) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Primetime DRMがファイアウォールの内側にある場合、Adobe Primetime DRMを実行するために使用されるアプリケーションサーバーとの間で、少なくとも2つのレベルにセグメント化が存在する必要があります。 外部ネットワークは、Webサーバーを含むDMZから分離し、Webサーバーは内部ネットワークから分離する必要があります。 これらの分離層は、ファイアウォールを使用して実装できます。 </p> <p>各ネットワーク層を通過するトラフィックを分類して制御し、必要最小限のデータのみが許可されるようにします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">プライベートIPアドレス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Primetime DRMアプリケーションサーバー上で、RFC 1918プライベートIPアドレスと共にNetwork Address Translation(NAT)を使用します。 プライベートIPアドレス(10.0.0.0/8、172.16.0.0/12および192.168.0.0/16)を割り当てると、攻撃者がインターネット経由でNAT内部ホストとの間でトラフィックをルーティングするのをより困難にすることができます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ファイアウォール </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ファイアウォールソリューションを選択する際に考慮すべき条件を次に示します。 </p> <p class="- topic/p "> 
     <ul class="- topic/ul " id="ul_wjf_lhz_n4"> 
      <li class="- topic/li " id="li_A620D0B635384590BA7804F9720D04D0">単純なパケットフィルタリングソリューションの代わりに、プロキシサーバやステートフル検査をサポートするファイアウォールを実装します。 </li> 
      <li class="- topic/li " id="li_3E4F814A30C047539185C23F4F57C282">セキュリティの枠組みをサポートするファイアウォールを使用し、明示的に許可されたサービスを除くすべてのサービスを拒否できます。 </li> 
      <li class="- topic/li " id="li_96160B3F14C4425397F017AF93FABE32">デュアルホームまたはマルチホームのファイアウォールソリューションを実装します。 このアーキテクチャは、最高レベルのセキュリティを提供し、不正なユーザーがファイアウォールセキュリティを迂回するのを防ぎます。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

