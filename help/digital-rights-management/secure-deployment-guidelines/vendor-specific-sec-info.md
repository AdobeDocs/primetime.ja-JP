---
description: オペレーティングシステムとアプリケーションサーバーは、Adobe Primetime DRMソリューションに含まれています。
seo-description: オペレーティングシステムとアプリケーションサーバーは、Adobe Primetime DRMソリューションに含まれています。
seo-title: ベンダー固有のセキュリティ情報
title: ベンダー固有のセキュリティ情報
uuid: 331baa42-5e19-40a5-bc74-0b1a2cb9370e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ベンダー固有のセキュリティ情報{#vendor-specific-security-information}

オペレーティングシステムとアプリケーションサーバーは、Adobe Primetime DRMソリューションに含まれています。

お使いのオペレーティングシステムとアプリケーションサーバーに関するベンダー固有のセキュリティ情報を確認するには、Adobe Primetime DRMキーサーバーの使用を参照してください。

## オペレーティングシステムのセキュリティ情報 {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

オペレーティングシステムを保護する場合は、オペレーティングシステムのベンダーが説明する対策を実装する必要があります。

以下に、対策の例を示します。

* ユーザー、役割、権限の定義と制御
* ログと監査証跡の監視
* 不要なサービスとアプリケーションの削除
* ファイルのバックアップ

Adobe Primetime DRMでサポートされるオペレーティングシステムに関する情報を以下に示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ベンダーのセキュリティパッチとアップグレードが適時に適用されない場合、権限のないユーザーがアプリケーションサーバーにアクセスするリスクが高くなります。 </p> <p>注意： セキュリティパッチを実稼働サーバーに適用する前に、必ずテストしてください。 </p> <p class="- topic/p ">定期的にパッチをチェックし、インストールするためのポリシーと手順を作成する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ウイルス対策ソフトウェア </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ウイルススキャナーは、署名や異常な動作をスキャンして、感染したファイルを識別できます。 </p> <p>スキャナーは、ウイルスの署名をファイルに保存します。通常、このファイルはローカルハードドライブに保存されます。 新しいウイルスは頻繁に検出されるので、このファイルを定期的に更新する必要があります。 これにより、ウイルススキャナーは常に最新のすべてのウイルスを識別できます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">NTP(Network Time Protocol) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">適切な運用とフォレンジック分析を行うために、Primetime DRMサーバーとパッケージャーで正確な時間を維持します。 安全なバージョンのNTPを使用して、インターネットに接続されているすべてのシステムでPrimetime DRM時刻を同期します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのセキュリティ情報 {#section_22986936F1A547CEAB2D97E9E9D4825C}

アプリケーションサーバーを保護する場合は、サーバーベンダーが説明する対策を実装する必要があります。

以下に、いくつかの対策を示します。

* 管理者のユーザー名が明確でない場合の使用
* 不要なサービスの無効化
* コンソールマネージャーの保護
* Cookieの保護の有効化
* 不要なポートを閉じる
* IPアドレスまたはドメインによる管理インターフェイスの制限
* Java™ Security Managerの使用

