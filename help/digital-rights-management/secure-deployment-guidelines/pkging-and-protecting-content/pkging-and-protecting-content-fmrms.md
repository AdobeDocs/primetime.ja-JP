---
description: FlashメディアRights ManagementServer 1.xとAdobe PrimetimeDRMは、異なるメタデータを使用してコンテンツをパッケージ化し、ライセンスを要求します。 Primetime DRMでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。
title: FlashメディアRights Managementサーバー1.xとの互換性の確保
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# FlashメディアRights Managementサーバ1.x {#ensuring-compatibility-with-flash-media-rights-management-server-x}との互換性の確保

FlashメディアRights ManagementServer 1.xとAdobe PrimetimeDRMは、異なるメタデータを使用してコンテンツをパッケージ化し、ライセンスを要求します。 Primetime DRMでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。

Primetime DRM SDKは、メタデータの変換に関する次のオプションをサポートしています。

* オフライン（推奨）

   オフラインプロセスでPrimetime DRMメタデータを生成し、クライアントから要求されるまでメタデータを保存します。 メタデータがオフラインで生成される場合、ライセンスサーバーは1.x CEKやPackagerの資格情報にアクセスする必要はありません。 License Serverでメタデータをリアルタイムで生成する必要がないので、オフラインオファーを変換すると、パフォーマンスが向上します。
* オンデマンド

   Primetime DRMメタデータは、クライアントによってメタデータが要求されたときに生成されます。 Primetime DRMクライアントがバージョン1.xのコンテンツをダウンロードすると、クライアントはDRMメタデータをPrimetime DRM SDKに送信します。 SDKは、DRMメタデータを現在の形式に変換し、メタデータにコンテンツ暗号化キー(CEK)を暗号化して埋め込み、コンテンツをPrimetime DRMクライアントに送り返します。

   >[!NOTE]
   >
   >Primetime DRM 1.xメタデータにはCEKが含まれていません。

   メタデータを変換するには、Primetime DRMでPrimetime DRM 1.xコンテンツ暗号化キーにアクセスする必要があります。 FlashメディアRights ManagementServer 1.xから移行する場合は、引き続きコンテンツ暗号化キーをLiveCycleESデータベースに保存するか、カスタムソリューションを実装してコンテンツ暗号化キーを別の場所に安全に保存できます。 コンテンツ暗号化キーをLiveCycleESデータベースに格納する場合は、**LiveCycle®ES2の堅牢化とセキュリティ**&#x200B;の&#x200B;*データベース*&#x200B;内の機密性の高いコンテンツへのアクセスの保護に概要を説明した推奨事項に従ってください。

FlashメディアRights ManagementServer 1.xを使用してパッケージ化されたコンテンツとの互換性を確保する方法について詳しくは、[Adobe PrimetimeAPIリファレンス](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References)のAdobe PrimetimeDRM APIを参照してください。
