---
description: Flash Media Rights Management Server 1.xの互換性に関連するリクエストには2種類あります。 1つのタイプのリクエストは、Adobe Primetime DRM 2.0以降をサポートするランタイムにアップグレードするように1.xクライアントに促すために使用されます。 ライセンスを要求する前に、1.xメタデータをPrimetime DRM形式に更新するためにもう1つ使用されます。 これらのリクエストのサポートは、FMRMS 1.0または1.5を使用するコンテンツを以前にデプロイした場合にのみ必要です。
seo-description: Flash Media Rights Management Server 1.xの互換性に関連するリクエストには2種類あります。 1つのタイプのリクエストは、Adobe Primetime DRM 2.0以降をサポートするランタイムにアップグレードするように1.xクライアントに促すために使用されます。 ライセンスを要求する前に、1.xメタデータをPrimetime DRM形式に更新するためにもう1つ使用されます。 これらのリクエストのサポートは、FMRMS 1.0または1.5を使用するコンテンツを以前にデプロイした場合にのみ必要です。
seo-title: FMRMSの互換性の処理
title: FMRMSの互換性の処理
uuid: c32ee087-2edf-4d11-be36-e2b31f3769de
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# FMRMSの互換性の処理 {#handling-fmrms-compatibility}

Flash Media Rights Management Server 1.xの互換性に関連するリクエストには2種類あります。 1つのタイプのリクエストは、Adobe Primetime DRM 2.0以降をサポートするランタイムにアップグレードするように1.xクライアントに促すために使用されます。 ライセンスを要求する前に、1.xメタデータをPrimetime DRM形式に更新するためにもう1つ使用されます。 これらのリクエストのサポートは、FMRMS 1.0または1.5を使用するコンテンツを以前にデプロイした場合にのみ必要です。

## クライアントのアップグレード {#upgrading-clients}

FMRMS 1.xクライアントがAdobe Primetime DRMサーバーに接続する場合、サーバーはクライアントにアップグレードを求めるプロンプトを表示する必要があります。

* リクエストハンドラークラスはで `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`す。
* リクエストURLは「1.x *コンテンツからのベースURL*」 + 「 [!DNL /edcws/services/urn:EDCLicenseService]」です

   他のAdobe Primetimeリクエストハンドラーとは異なり、このハンドラーはリクエスト情報へのアクセスを提供せず、応答データの設定を必須とします。 のインスタンスを作 `FMRMSv1RequestHandler`成し、 `close()`

## メタデータのアップグレード {#upgrading-metadata}

Adobe Primetime DRMクライアントは、Flash Media Rights Management Server 1.xでパッケージ化されたコンテンツを検出し、そのコンテンツから暗号化メタデータを抽出してサーバーに送信します。 次に、サーバーはFMRMS 1.xメタデータをPrimetime DRM形式に変換し、クライアントに送信します。 次に、クライアントは、更新されたメタデータを標準のPrimetime DRMライセンスリクエストで送信します。

* リクエストハンドラークラスはで `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`す。
* リクエストURLは「1.x *コンテンツからのベースURL*」「+」 [!DNL /flashaccess/headerconversion/v1]です。

サーバがクライアントから古いメタデータを受け取ると、メタデータの変換はその場で行われます。 また、サーバは古いコンテンツを事前に処理し、変換されたメタデータを保存することもできます。この場合、クライアントが新しいメタデータを要求すると、サーバは古いメタデータのライセンス識別子に一致する新しいメタデータを取得する必要があります。

メタデータを変換するには、サーバーは次の手順を実行する必要があります。

* 取得 `LiveCycleKeyMetaData`。 メタデータを事前に変換するに `LiveCycleKeyMetaData` は、を使用して1.xパッケージファイルから取得しま `MediaEncrypter.examineEncryptedContent()`す。 メタデータは、メタデータ変換要求( `FMRMSv1MetadataHandler.getOriginalMetadata()`)にも含まれます。

* 古いメタデータからライセンス識別子を取得し、暗号化キーとDRMポリシーを探します（この情報は、元々はAdobe LiveCycle ESデータベースにありました）。 LiveCycle ES DRMポリシーは、Primetime DRM 2.0 DRMポリシーに変換する必要があります。)リファレンスの実装には、DRMポリシーを変換し、LiveCycle ESからライセンス情報を書き出すためのスクリプトとサンプルコードが含まれています。
* (を呼び出して取 `V2KeyParameters` 得した)オブジェクトを入力 `MediaEncrypter.getKeyParameters()`します。

* 暗号化メタデ `SigningCredential`ータの署名に使用されるAdobeによって発行されるPackagerの秘密鍵証明書であるを読み込みます。 を呼び出して、 `SignatureParameters` 署名の秘密鍵証明書を `MediaEncrypter.getSignatureParameters()` 入力することで、オブジェクトを取得します。

* を取得す `MetaDataConverter.convertMetadata()` るための呼び出し `V2ContentMetaData`。

* 今後使用 `V2ContentMetaData.getBytes()` するために電話および保存するか、電話でお問い合わせくださ `FMRMSv1MetadataHandler.setUpdatedMetadata()`い。