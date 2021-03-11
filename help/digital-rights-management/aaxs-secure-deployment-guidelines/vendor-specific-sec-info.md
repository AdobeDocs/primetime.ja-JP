---
title: ベンダー固有のセキュリティ情報
description: ベンダー固有のセキュリティ情報
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ベンダー固有のセキュリティ情報{#vendor-specific-security-information}

この節では、Adobeアクセスソリューションに組み込まれるオペレーティングシステムとアプリケーションサーバーに関するセキュリティ関連情報を説明します。

この節に示すリンクを使用して、お使いのオペレーティングシステムとアプリケーションサーバーに関するベンダー固有のセキュリティ情報を検索します。

## オペレーティングシステムのセキュリティ情報{#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

オペレーティングシステムを保護する際は、オペレーティングシステムのベンダーが挙げている対策を慎重に実装してください。具体的には、次のような対策が行われます。

* ユーザー、ロール、権限の定義と制御
* ログと監査記録の監視
* 不要なサービスとアプリケーションの削除
* ファイルのバックアップ

Adobeアクセスがサポートするオペレーティングシステムのセキュリティ情報については、次の表の資料を参照してください。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-ugl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">オペレーティングシステム </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">セキュリティリソース </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Enterprise EditionまたはStandard Edition </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Windows Server 2008セキュリティガイド</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4、5.5、5.6。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Red Hat Enterprise Linux 5セキュリティガイド</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

次の表では、オペレーティングシステムに存在するセキュリティの脆弱性を最小限に抑えるための方法について説明します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ベンダーのセキュリティパッチとアップグレードが迅速に適用されない場合、権限のないユーザーがアプリケーションサーバーにアクセスするリスクが高まります。 実稼働サーバーにセキュリティパッチを適用する前に、テストしてください。 </p> <p class="- topic/p ">また、パッチを定期的にチェックし、インストールするためのポリシーと手順を作成します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ウイルス対策ソフトウェア </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ウイルススキャンプログラムは、署名をスキャンするか、異常な動作を監視することで、感染したファイルを識別できます。 スキャンプログラムは、ウイルスの署名をファイルに保存します。通常、このファイルはローカルハードドライブに保存されます。 新しいウイルスは頻繁に発見されるので、ウイルススキャナーが現在のすべてのウイルスを識別できるように、頻繁にこのファイルを更新する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Network Time Protocol（NTP；ネットワークタイムプロトコル） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">適切な運用とフォレンジック分析の両方を行うために、AdobeアクセスサーバーとAdobeアクセスパッケージャーで正確な時間を維持します。 インターネットに接続されているすべてのシステムの時刻を同期するには、安全なバージョンのNTPを使用します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのセキュリティ情報{#section-EBB4EF371CFF4A848694CC240B23D404}

アプリケーションサーバーを保護する場合は、サーバーのベンダーが挙げている対策を実装する必要があります。対策には、次のものがあります。

* 管理者ユーザー名が明確でない場合の使用
* 不要なサービスを無効にする
* コンソールマネージャーを保護する
* cookieの保護を有効にする
* 不要なポートを閉じる
* IPアドレスまたはドメインによる管理インターフェイスの制限
* Java™ Security Managerの使用

