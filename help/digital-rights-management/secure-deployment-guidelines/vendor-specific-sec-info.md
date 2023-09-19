---
description: オペレーティングシステムとアプリケーションサーバーは、Adobe Primetime DRM ソリューションに含まれています。
title: ベンダー固有のセキュリティ情報
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ベンダー固有のセキュリティ情報{#vendor-specific-security-information}

オペレーティングシステムとアプリケーションサーバーは、Adobe Primetime DRM ソリューションに含まれています。

オペレーティングシステムとアプリケーションサーバーに関するベンダー固有のセキュリティ情報を確認するには、 Adobe Primetime DRM キーサーバーの使用を参照してください。

## オペレーティングシステムのセキュリティ情報 {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

オペレーティングシステムを保護する場合は、オペレーティングシステムのベンダーが説明する対策を実装する必要があります。

次に、いくつかの測定を示します。

* ユーザー、役割および権限の定義と制御
* ログと監査記録の監視
* 不要なサービスやアプリケーションの削除
* ファイルのバックアップ

Adobe Primetime DRM でサポートされているオペレーティングシステムに関する情報を以下に示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ugl_kjz_n4"> 
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

オペレーティングシステムのセキュリティの脆弱性を最小限に抑える方法に関する情報を次に示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ベンダーのセキュリティパッチとアップグレードが適時に適用されない場合、権限のないユーザーがアプリケーションサーバーにアクセスするリスクが高まります。 </p> <p>注意：セキュリティパッチを本番サーバに適用する前に、必ずテストしてください。 </p> <p class="- topic/p ">パッチを定期的にチェックしてインストールするには、ポリシーと手順を作成する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ウイルス対策ソフトウェア </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ウイルススキャナは、署名または異常な動作をスキャンすることで、感染したファイルを識別できます。 </p> <p>スキャナーは、ウイルスの署名をファイルに保存します。このファイルは通常、ローカルのハードドライブに保存されます。 新しいウイルスは頻繁に発見されるので、このファイルを定期的に更新する必要があります。 これにより、ウイルススキャナは常に最新のウイルスを識別できます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ネットワークタイムプロトコル (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">適切な操作と法医学的分析をおこなうために、Primetime DRM サーバーとパッケージャーで正確な時間を保ちます。 安全なバージョンの NTP を使用して、インターネットに接続されているすべてのシステムで Primetime DRM 時間を同期します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのセキュリティ情報 {#section_22986936F1A547CEAB2D97E9E9D4825C}

アプリケーションサーバーを保護する場合は、サーバーベンダーが説明する対策を実装する必要があります。

以下に、その対策の一部を示します。

* 不明な管理者ユーザー名の使用
* 不要なサービスの無効化
* コンソールマネージャーの保護
* セキュリティで保護された cookie の有効化
* 不要なポートを閉じる
* IP アドレスまたはドメインによる管理インターフェイスの制限
* Java™ Security Manager の使用
