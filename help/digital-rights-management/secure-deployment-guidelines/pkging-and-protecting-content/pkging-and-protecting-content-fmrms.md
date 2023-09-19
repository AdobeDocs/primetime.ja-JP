---
description: FlashメディアRights Managementサーバー 1.x とAdobe Primetime DRM は、異なるメタデータを使用して、コンテンツをパッケージ化し、ライセンスをリクエストします。 Primetime DRM で FMRMS バージョン 1.x のコンテンツを使用するには、メタデータを変換する必要があります。
title: FlashメディアRights Managementサーバー 1.x との互換性の確保
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# FlashメディアRights Managementサーバー 1.x との互換性の確保 {#ensuring-compatibility-with-flash-media-rights-management-server-x}

FlashメディアRights Managementサーバー 1.x とAdobe Primetime DRM は、異なるメタデータを使用して、コンテンツをパッケージ化し、ライセンスをリクエストします。 Primetime DRM で FMRMS バージョン 1.x のコンテンツを使用するには、メタデータを変換する必要があります。

Primetime DRM SDK では、メタデータの変換に次のオプションをサポートしています。

* オフライン（推奨）

  Primetime DRM メタデータをオフラインプロセスで生成し、クライアントから要求されるまでメタデータを保存します。 メタデータがオフラインで生成される場合、ライセンスサーバーは 1.x CEK や Packager の資格情報にアクセスする必要はありません。 ライセンスサーバーはメタデータをリアルタイムで生成する必要がないので、オフラインの変換はパフォーマンスが向上します。
* オンデマンド

  Primetime DRM メタデータは、クライアントによってメタデータが要求されたときに生成されます。 Primetime DRM クライアントがバージョン 1.x のコンテンツをダウンロードすると、クライアントは DRM メタデータを Primetime DRM SDK に送信します。 SDK は、DRM メタデータを現在の形式に変換し、メタデータにコンテンツ暗号化キー (CEK) を暗号化して埋め込み、コンテンツを Primetime DRM クライアントに返します。

  >[!NOTE]
  >
  >Primetime DRM 1.x メタデータには CEK が含まれていません。

  メタデータを変換するには、Primetime DRM で Primetime DRM 1.x のコンテンツ暗号化キーにアクセスする必要があります。 FlashMediaRights Managementサーバー 1.x から移行する場合、コンテンツ暗号化キーをLiveCycleES データベースに引き続き保存するか、カスタムソリューションを実装して、コンテンツ暗号化キーを別の場所に安全に保存できます。 コンテンツ暗号化キーをLiveCycleES データベースに格納する場合は、 *データベース内の機密コンテンツへのアクセスの保護* in **LiveCycle® ES2 の堅牢化とセキュリティ**.

Media Media MediaRights ManagementServer 1.x を使用してパッケージ化されたコンテンツとの互換性を確保する方法について詳しくは、 [Adobe Primetime API リファレンス](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).
