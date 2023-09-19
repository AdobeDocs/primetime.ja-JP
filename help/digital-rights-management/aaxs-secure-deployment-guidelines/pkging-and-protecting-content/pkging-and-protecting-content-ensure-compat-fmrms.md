---
title: FlashMediaRights ManagementServer 1.x との互換性を確保する
description: FlashMediaRights ManagementServer 1.x との互換性を確保する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# FlashMediaRights ManagementServer 1.x との互換性を確保する{#ensure-compatibility-with-flash-media-rights-management-server-x}

FlashメディアRights Managementサーバー 1.x とAdobeアクセスでは、コンテンツのパッケージ化とライセンスのリクエストに異なるメタデータを使用します。 Adobeアクセスで FMRMS バージョン 1.x コンテンツを使用するには、メタデータを変換する必要があります。

Adobeアクセス SDK では、メタデータの変換に関して次の 2 つのオプションがサポートされています。

* オフライン（推奨）

  オフラインプロセスでAdobeアクセスメタデータを生成し、クライアントが要求したときに使用するために保存します。 Adobeでは、このオプションを推奨しています。 メタデータがオフラインで生成される場合、ライセンスサーバーは 1.x CEK や Packager の資格情報にアクセスする必要はありません。 また、License Server はメタデータをリアルタイムで生成する必要がないので、オフラインでの変換はパフォーマンスが向上します。

* オンデマンド

  クライアントが要求したときに、Adobeアクセスメタデータをオンデマンドで生成します。 Adobeアクセスクライアントがバージョン 1.x のコンテンツをダウンロードすると、DRM メタデータ（DRM ヘッダーとも呼ばれます）がAdobeアクセス SDK に送信されます。 SDK は DRM メタデータを現在の形式に変換します。 SDK は、コンテンツ暗号化キー (CEK) をメタデータに暗号化して埋め込み、コンテンツをAdobeアクセスクライアントに送り返します。 (AdobeAccess 1.x のメタデータには CEK が含まれていません )。

  メタデータを変換するには、AdobeアクセスでAdobeAccess 1.x のコンテンツ暗号化キーにアクセスする必要があります。 FlashMediaRights Managementサーバー 1.x から移行する場合、コンテンツ暗号化キーをLiveCycleES データベースに引き続き保存するか、カスタムソリューションを実装して安全にコンテンツ暗号化キーを他の場所に保存することができます。 コンテンツ暗号化キーをLiveCycleES データベースに保存し続ける場合は、「データベース内の機密コンテンツへのアクセスの保護」で説明されている推奨事項に従ってください。詳しくは、 *LiveCycleES の堅牢化とセキュリティ*.

Media Media Media Server 1.x を使用してパッケージ化されたコンテンツとの互換性を確保する方法について詳しくは、FlashメディアRights Managementサーバー 1.x の *Adobeアクセス API リファレンス*.
