---
title: ベンダー固有のセキュリティ情報
description: ベンダー固有のセキュリティ情報
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ベンダー固有のセキュリティ情報{#vendor-specific-security-information}

この節では、Adobe・アクセス・ソリューションに組み込まれるオペレーティング・システムおよびアプリケーション・サーバーに関するセキュリティ関連の情報を示します。

この節に示すリンクを使用して、オペレーティングシステムとアプリケーションサーバーに関するベンダー固有のセキュリティ情報を検索します。

## オペレーティングシステムのセキュリティ情報 {#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

オペレーティングシステムを保護する場合は、次のように、オペレーティングシステムのベンダーが説明する対策を慎重に実装します。

* ユーザー、役割および権限の定義と制御
* ログと監査記録の監視
* 不要なサービスやアプリケーションの削除
* ファイルのバックアップ

Adobe・アクセスがサポートするオペレーティング・システムのセキュリティ情報については、次の表のリソースを参照してください。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-ugl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">オペレーティングシステム </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">セキュリティリソース </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Enterprise または Standard Edition </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Windows Server 2008 セキュリティガイド</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4、5.5、および 5.6。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Red Hat Enterprise Linux 5 セキュリティガイド</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

次の表に、オペレーティングシステムに存在するセキュリティの脆弱性を最小限に抑えるための潜在的なアプローチを示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-whl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">項目 </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">セキュリティパッチ </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ベンダーのセキュリティパッチとアップグレードが適時に適用されない場合、権限のないユーザーがアプリケーションサーバーにアクセスするリスクが高まります。 セキュリティパッチを本番サーバに適用する前に、テストを実施してください。 </p> <p class="- topic/p ">また、定期的にパッチをチェックしてインストールするポリシーと手順を作成します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ウイルス対策ソフトウェア </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ウイルススキャナは、署名をスキャンするか、異常な動作を監視することで、感染したファイルを識別できます。 スキャナーは、ウイルスの署名をファイルに保存します。このファイルは通常、ローカルのハードドライブに保存されます。 新しいウイルスは頻繁に発見されるので、ウイルススキャナが現在のウイルスをすべて識別するには、このファイルを頻繁に更新する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ネットワークタイムプロトコル (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">適切な操作と法医学的分析の両方を行うために、AdobeアクセスサーバーとAdobeアクセスパッケージャーの正確な時間を保ちます。 インターネットに接続されているすべてのシステムの時刻を同期するには、安全なバージョンの NTP を使用します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのセキュリティ情報 {#section-EBB4EF371CFF4A848694CC240B23D404}

アプリケーションサーバーを保護する場合は、サーバーベンダーが説明する以下の対策を実装する必要があります。

* 不明な管理者ユーザー名の使用
* 不要なサービスの無効化
* コンソールマネージャーの保護
* セキュリティで保護された cookie の有効化
* 不要なポートを閉じる
* IP アドレスまたはドメインによる管理インターフェイスの制限
* Java™ Security Manager の使用
