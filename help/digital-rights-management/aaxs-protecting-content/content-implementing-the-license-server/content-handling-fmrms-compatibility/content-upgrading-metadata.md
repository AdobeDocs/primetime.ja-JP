---
title: メタデータのアップグレード
description: メタデータのアップグレード
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# メタデータのアップグレード{#upgrading-metadata}

AdobeアクセスクライアントがFlashメディアRights Managementサーバー 1.x でパッケージ化されたコンテンツを検出した場合、そのコンテンツから暗号化メタデータを抽出し、サーバーに送信します。 サーバーは FMRMS 1.x メタデータをAdobeアクセス形式に変換し、クライアントに返します。 次に、クライアントは、更新されたメタデータを標準のAdobeアクセスライセンスリクエストで送信します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* リクエスト URL は「*1.x コンテンツからのベース URL*&quot; +&quot;/flashaccess/headerconversion/v1&quot;

サーバが古いメタデータをクライアントから受け取ると、メタデータの変換がオンザフライでおこなわれる可能性があります。 また、サーバは古いコンテンツを前処理し、変換されたメタデータを保存することもできます。この場合、クライアントが新しいメタデータを要求すると、サーバは古いメタデータのライセンス識別子に一致する新しいメタデータを取得するだけです。

メタデータを変換するには、サーバーが次の手順を実行する必要があります。

* 取得 `LiveCycleKeyMetaData`. メタデータを事前に変換するには、次の手順を実行します。 `LiveCycleKeyMetaData` は、 `MediaEncrypter.examineEncryptedContent()`. このメタデータは、メタデータ変換要求 ( `FMRMSv1MetadataHandler.getOriginalMetadata()`) をクリックします。
* 古いメタデータからライセンス識別子を取得し、暗号化キーとポリシーを見つけます ( この情報は元々AdobeLiveCycleES データベースにありました )。 LiveCycleES ポリシーは、AdobeAccess 2.0 ポリシーに変換する必要があります。) リファレンス実装には、ポリシーを変換し、LiveCycleES からライセンス情報を書き出すためのスクリプトとサンプルコードが含まれています。
* 次の項目に入力： `V2KeyParameters` を呼び出して取得するオブジェクト `MediaEncrypter.getKeyParameters()`) をクリックします。
* を読み込む `SigningCredential`：暗号化メタデータの署名に使用されるAdobeが発行する packager 秘密鍵証明書です。 を取得します `SignatureParameters` を呼び出すことで、 `MediaEncrypter.getSignatureParameters()` 署名証明書に入力します。
* 通話 `MetaDataConverter.convertMetadata()` 手に入れる `V2ContentMetaData`.
* 通話 `V2ContentMetaData.getBytes()` またはを後で使用するために保存するか、呼び出します。 `FMRMSv1MetadataHandler.setUpdatedMetadata()`.
