---
seo-title: メタデータのアップグレード
title: メタデータのアップグレード
uuid: 769483e6-a2d1-46cb-afcf-557aa807037c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# メタデータのアップグレード{#upgrading-metadata}

Adobe Primetime DRMクライアントは、Flash Media Rights Management Server 1.xでパッケージ化されたコンテンツを検出し、そのコンテンツから暗号化メタデータを抽出してサーバーに送信します。 次に、サーバーはFMRMS 1.xメタデータをPrimetime DRM形式に変換し、クライアントに送信します。 次に、クライアントは、更新されたメタデータを標準のPrimetime DRMライセンスリクエストで送信します。

* リクエストハンドラークラスはで `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`す。
* リクエストURLは「1.x *コンテンツからのベースURL*」 + [!DNL /flashaccess/headerconversion/v1]&quot;です。

サーバがクライアントから古いメタデータを受け取ると、メタデータの変換はその場で行われます。 また、サーバは古いコンテンツを事前に処理し、変換されたメタデータを保存することもできます。この場合、クライアントが新しいメタデータを要求すると、サーバは古いメタデータのライセンス識別子に一致する新しいメタデータを取得する必要があります。

メタデータを変換するには、サーバーは次の手順を実行する必要があります。

* 取得 `LiveCycleKeyMetaData`。 メタデータを事前に変換するに `LiveCycleKeyMetaData` は、を使用して1.xパッケージファイルから取得しま `MediaEncrypter.examineEncryptedContent()`す。 メタデータは、メタデータ変換要求( `FMRMSv1MetadataHandler.getOriginalMetadata()`)にも含まれます。

* 古いメタデータからライセンス識別子を取得し、暗号化キーとDRMポリシーを探します（この情報は、元々はAdobe LiveCycle ESデータベースにありました）。 LiveCycle ES DRMポリシーは、Primetime DRM 2.0 DRMポリシーに変換する必要があります。)リファレンスの実装には、DRMポリシーを変換し、LiveCycle ESからライセンス情報を書き出すためのスクリプトとサンプルコードが含まれています。
* (を呼び出して取 `V2KeyParameters` 得した)オブジェクトを入力 `MediaEncrypter.getKeyParameters()`します。

* 暗号化メタデ `SigningCredential`ータの署名に使用されるAdobeによって発行されるPackagerの秘密鍵証明書であるを読み込みます。 を呼び出して、 `SignatureParameters` 署名の秘密鍵証明書を `MediaEncrypter.getSignatureParameters()` 入力することで、オブジェクトを取得します。

* を取得す `MetaDataConverter.convertMetadata()` るための呼び出し `V2ContentMetaData`。

* 今後使用 `V2ContentMetaData.getBytes()` するために電話および保存するか、電話でお問い合わせくださ `FMRMSv1MetadataHandler.setUpdatedMetadata()`い。

