---
seo-title: FlashメディアRights Managementサーバー1.xとの互換性の確認
title: FlashメディアRights Managementサーバー1.xとの互換性の確認
uuid: 0160ca02-ebe6-4090-bf32-1d1a46088844
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# FlashメディアRights Managementサーバー1.x{#ensure-compatibility-with-flash-media-rights-management-server-x}との互換性を確認する

FlashメディアRights Managementサーバー1.xとAdobeアクセスは、コンテンツのパッケージ化とライセンスの要求に異なるメタデータを使用します。 AdobeアクセスでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。

AdobeアクセスSDKは、メタデータの変換に関する次の2つのオプションをサポートしています。

* オフライン（推奨）

   オフラインプロセスでAdobeアクセスメタデータを生成し、クライアントから要求された場合に使用するために保存します。 Adobeが推奨するオプションです。 メタデータがオフラインで生成される場合、ライセンスサーバーは1.x CEKやPackagerの資格情報にアクセスする必要はありません。 さらに、License Serverでメタデータをリアルタイムで生成する必要がないので、オフラインオファーの変換によるパフォーマンスが向上します。

* オンデマンド

   クライアントが要求した場合に、Adobeアクセスメタデータをオンデマンドで生成します。 バージョン1.xのコンテンツをAdobeアクセスクライアントがダウンロードすると、DRMメタデータ（DRMヘッダー）がAdobeアクセスSDKに送信されます。 SDKは、DRMメタデータを現在の形式に変換します。 SDKは、コンテンツ暗号化キー(CEK)を暗号化してメタデータに埋め込み、コンテンツをAdobeアクセスクライアントに送り返します。 (Adobeアクセス1.xのメタデータにはCEKが含まれていません)。

   メタデータを変換するには、AdobeアクセスでAdobeAccess 1.xのコンテンツ暗号化キーにアクセスする必要があります。 FlashメディアRights Managementサーバー1.xから移行する場合は、引き続きコンテンツ暗号化キーをLiveCycleESデータベースに格納できます。また、カスタムソリューションを導入して、コンテンツ暗号化キーを安全に他の場所に保存することもできます。 コンテンツ暗号化キーをLiveCycleESデータベースに格納し続ける場合は、*LiveCycleES*&#x200B;の堅牢化とセキュリティの「データベース内の機密コンテンツへのアクセスの保護」に記載されている推奨事項に従ってください。

FlashメディアRights Managementサーバー1.xを使用してパッケージ化されたコンテンツとの互換性を確保する方法について詳しくは、『*AdobeアクセスAPIリファレンス*』を参照してください。
