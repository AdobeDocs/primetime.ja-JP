---
seo-title: ベンダー固有のセキュリティ情報
title: ベンダー固有のセキュリティ情報
uuid: 23186770-c73a-4802-bc30-fa9e4b47d9ba
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ベンダー固有のセキュリティ情報{#vendor-specific-security-information}

この節では、Adobe Accessソリューションに組み込まれるオペレーティングシステムとアプリケーションサーバーに関するセキュリティ関連の情報を説明します。

この節に示すリンクを使用して、ご使用のオペレーティングシステムおよびアプリケーションサーバーに関するベンダー固有のセキュリティ情報を検索します。

## オペレーティングシステムのセキュリティ情報 {#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

オペレーティングシステムを保護する際は、次のようなオペレーティングシステムのベンダーが説明する対策を慎重に実装します。

* ユーザー、役割、権限の定義と制御
* ログと監査証跡の監視
* 不要なサービスとアプリケーションの削除
* ファイルのバックアップ

Adobe Accessがサポートするオペレーティングシステムのセキュリティ情報については、次の表の資料を参照してください。

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

次の表では、オペレーティングシステムに存在するセキュリティの脆弱性を最小限に抑えるための考えられる方法を説明します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ベンダーのセキュリティパッチとアップグレードが適時に適用されない場合、権限のないユーザーがアプリケーションサーバーにアクセスするリスクが高まります。 セキュリティパッチを実稼働サーバーに適用する前にテストします。 </p> <p class="- topic/p ">また、パッチを定期的にチェックし、インストールするためのポリシーと手順を作成します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ウイルス対策ソフトウェア </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ウイルススキャナーは、署名をスキャンするか、異常な動作を監視することで、感染したファイルを識別できます。 スキャナーは、ウイルスの署名をファイルに保存します。通常、このファイルはローカルハードドライブに保存されます。 新しいウイルスは頻繁に発見されるので、ウイルススキャナーが現在のすべてのウイルスを識別できるように、このファイルを頻繁に更新する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">NTP(Network Time Protocol) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">適切な運用とフォレンジック分析の両方を行うために、Adobe AccessサーバーとAdobe Accessパッケージャーで正確な時間を確保します。 安全なバージョンのNTPを使用して、インターネットに接続されているすべてのシステムの時刻を同期します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## アプリケーションサーバーのセキュリティ情報 {#section-EBB4EF371CFF4A848694CC240B23D404}

アプリケーションサーバーを保護する場合は、サーバーベンダーが説明する以下の対策を実装する必要があります。

* 管理者のユーザー名が明確でない場合の使用
* 不要なサービスの無効化
* コンソールマネージャーの保護
* Cookieの保護の有効化
* 不要なポートを閉じる
* IPアドレスまたはドメインによる管理インターフェイスの制限
* Java™ Security Managerの使用

