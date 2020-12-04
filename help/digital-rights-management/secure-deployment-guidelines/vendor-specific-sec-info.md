---
description: オペレーティングシステムとアプリケーションサーバーは、Adobe PrimetimeDRMソリューションに含まれています。
seo-description: オペレーティングシステムとアプリケーションサーバーは、Adobe PrimetimeDRMソリューションに含まれています。
seo-title: ベンダー固有のセキュリティ情報
title: ベンダー固有のセキュリティ情報
uuid: 331baa42-5e19-40a5-bc74-0b1a2cb9370e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# ベンダー固有のセキュリティ情報{#vendor-specific-security-information}

オペレーティングシステムとアプリケーションサーバーは、Adobe PrimetimeDRMソリューションに含まれています。

お使いのオペレーティングシステムとアプリケーションサーバーに関するベンダー固有のセキュリティ情報については、「Adobe PrimetimeDRMキーサーバーの使用」を参照してください。

## オペレーティングシステムのセキュリティ情報{#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

オペレーティングシステムを保護する場合は、オペレーティングシステムのベンダーが説明する対策を実装する必要があります。

以下に、その対策の一部を示します。

* ユーザー、ロール、権限の定義と制御
* ログと監査記録の監視
* 不要なサービスとアプリケーションの削除
* ファイルのバックアップ

Adobe PrimetimeDRMでサポートされるオペレーティングシステムに関する情報を以下に示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ugl_kjz_n4"> 
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

オペレーティングシステムのセキュリティの脆弱性を最小限に抑える方法について、次に説明します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_whl_kjz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">項目 </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">セキュリティパッチ </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ベンダーのセキュリティパッチとアップグレードが迅速に適用されない場合、権限のないユーザーがアプリケーションサーバーにアクセスするリスクが高まります。 </p> <p>注意： 実稼働サーバーにセキュリティパッチを適用する前に、必ずセキュリティパッチをテストしてください。 </p> <p class="- topic/p ">パッチを定期的にチェックしてインストールするには、ポリシーと手順を作成する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ウイルス対策ソフトウェア </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ウイルススキャンプログラムは、署名や異常な動作をスキャンして、感染したファイルを識別することができます。 </p> <p>スキャンプログラムは、ウイルスの署名をファイルに保存します。通常、このファイルはローカルハードドライブに保存されます。 新しいウイルスは頻繁に検出されるので、このファイルを定期的に更新する必要があります。 これにより、ウイルススキャナは常に現在のすべてのウイルスを識別できます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Network Time Protocol（NTP；ネットワークタイムプロトコル） </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">適切な操作とフォレンジック分析を行うために、Primetime DRMサーバーおよびパッケージャーの正確な時間を維持します。 安全なバージョンのNTPを使用して、インターネットに接続されているすべてのシステムのPrimetime DRM時間を同期します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのセキュリティ情報{#section_22986936F1A547CEAB2D97E9E9D4825C}

アプリケーションサーバーを保護する場合は、サーバーのベンダーが挙げている対策を実装する必要があります。

以下に、その対策の例を示します。

* 管理者ユーザー名が明確でない場合の使用
* 不要なサービスを無効にする
* コンソールマネージャーを保護する
* cookieの保護を有効にする
* 不要なポートを閉じる
* IPアドレスまたはドメインによる管理インターフェイスの制限
* Java™ Security Managerの使用

