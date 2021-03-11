---
title: メタデータのアップグレード
description: メタデータのアップグレード
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# メタデータをアップグレード中{#upgrading-metadata}

Adobeアクセスクライアントは、FlashメディアRights Managementサーバー1.xでパッケージ化されたコンテンツを検出すると、コンテンツから暗号化メタデータを抽出し、サーバーに送信します。 サーバは、FMRMS 1.xメタデータをAdobeアクセス形式に変換して、クライアントに送り返します。 次に、クライアントは、更新されたメタデータを標準Adobeアクセスライセンス要求で送信します。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`です。
* リクエストURLは、「*1.x content*&#x200B;からのベースURL」 +「/flashaccess/headerconversion/v1」です。

メタデータの変換は、サーバがクライアントから古いメタデータを受け取ったときに、その場で実行できます。 または、サーバは古いコンテンツを事前に処理し、変換されたメタデータを保存することができます。この場合、クライアントが新しいメタデータを要求すると、サーバは、古いメタデータのライセンス識別子に一致する新しいメタデータを取得するだけです。

メタデータを変換するには、サーバーは次の手順を実行する必要があります。

* `LiveCycleKeyMetaData`を取得します。 メタデータを事前に変換するには、`MediaEncrypter.examineEncryptedContent()`を使用して1.xパッケージファイルから`LiveCycleKeyMetaData`を取得します。 メタデータは、メタデータ変換要求(`FMRMSv1MetadataHandler.getOriginalMetadata()`)にも含まれます。
* 古いメタデータからライセンス識別子を取得し、暗号化キーとポリシーを探します(この情報は、元々AdobeLiveCycleESデータベースにあったものです)。 LiveCycleのESポリシーは、Adobeアクセス2.0ポリシーに変換する必要があります。) リファレンスの実装には、ポリシーを変換し、LiveCycleESからライセンス情報を書き出すためのスクリプトとサンプルコードが含まれています。
* `V2KeyParameters`オブジェクトを入力します（`MediaEncrypter.getKeyParameters()`を呼び出して取得します）。
* `SigningCredential`を読み込みます。これは、暗号化メタデータの署名に使用されるAdobeによって発行されるパッケージャーの秘密鍵証明書です。 `MediaEncrypter.getSignatureParameters()`を呼び出して`SignatureParameters`オブジェクトを取得し、署名の秘密鍵証明書を入力します。
* `MetaDataConverter.convertMetadata()`を呼び出して`V2ContentMetaData`を取得します。
* `V2ContentMetaData.getBytes()`を呼び出して将来的に使用するためにストアを呼び出すか、`FMRMSv1MetadataHandler.setUpdatedMetadata()`を呼び出します。

