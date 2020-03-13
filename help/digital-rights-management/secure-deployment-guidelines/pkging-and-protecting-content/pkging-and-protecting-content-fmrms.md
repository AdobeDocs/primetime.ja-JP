---
description: Flash Media Rights Management Server 1.xとAdobe Primetime DRMは、異なるメタデータを使用して、コンテンツのパッケージ化とライセンスの要求を行います。 Primetime DRMでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。
seo-description: Flash Media Rights Management Server 1.xとAdobe Primetime DRMは、異なるメタデータを使用して、コンテンツのパッケージ化とライセンスの要求を行います。 Primetime DRMでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。
seo-title: Flash Media Rights Management Server 1.xとの互換性の確保
title: Flash Media Rights Management Server 1.xとの互換性の確保
uuid: dd70941e-9015-4fb0-b265-557b6252e051
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Flash Media Rights Management Server 1.xとの互換性の確保 {#ensuring-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.xとAdobe Primetime DRMは、異なるメタデータを使用して、コンテンツのパッケージ化とライセンスの要求を行います。 Primetime DRMでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。

Primetime DRM SDKは、メタデータの変換に関する次のオプションをサポートしています。

* オフライン（推奨）

   オフラインプロセスでPrimetime DRMメタデータを生成し、クライアントから要求されるまでメタデータを保存します。 メタデータがオフラインで生成される場合、ライセンスサーバーは1.x CEKやPackagerの秘密鍵証明書にアクセスする必要はありません。 License Serverでメタデータをリアルタイムで生成する必要がないので、オフラインの変換により、パフォーマンスが向上します。
* オンデマンド

   Primetime DRMメタデータは、メタデータがクライアントによって要求されたときに生成されます。 Primetime DRMクライアントがバージョン1.xのコンテンツをダウンロードすると、クライアントはDRMメタデータをPrimetime DRM SDKに送信します。 SDKは、DRMメタデータを現在の形式に変換し、コンテンツ暗号化キー(CEK)を暗号化してメタデータに埋め込み、コンテンツをPrimetime DRMクライアントに返送します。

   >[!NOTE]
   >
   >Primetime DRM 1.xメタデータにはCEKが含まれていません。

   メタデータを変換するには、Primetime DRMでPrimetime DRM 1.xコンテンツ暗号化キーへのアクセスが必要です。 Flash Media Rights Management Server 1.xから移行する場合は、引き続きコンテンツ暗号化キーをLiveCycle ESデータベースに保存するか、カスタムソリューションを実装して、コンテンツ暗号化キーを別の場所に安全に保存できます。 コンテンツ暗号化キーをLiveCycle ESデータベースに保存する場合は、 *Protecting access to sensitive content in the database* （LiveCycle® ES2の堅牢化とセキュリティ）で概要を説明している推奨事項に従ってください ****。

Flash Media Rights Management Server 1.xを使用してパッケージ化されたコンテンツとの互換性を確保する方法について詳しくは、 [Adobe Primetime APIリファレンスのAdobe Primetime DRM APIを参照してください](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References)。
