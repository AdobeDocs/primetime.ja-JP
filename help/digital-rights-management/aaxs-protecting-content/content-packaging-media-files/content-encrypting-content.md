---
seo-title: コンテンツの暗号化
title: コンテンツの暗号化
uuid: ea71154e-557b-447e-bc14-208232f00be1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コンテンツの暗号化{#encrypting-content}

FLVおよびF4Vコンテンツの暗号化には、オブジェクトの使用が含ま `MediaEncrypter` れます。 また、オーディオトラックのみを含むFLVおよびF4Vファイルをパッケージ化することもできます。 ローエンドデバイス用にH.264コンテンツを暗号化する場合、パフォーマンスを向上させるために部分的な暗号化のみを適用するのが実用的な場合があります。 この場合、F4Vファイルは、この方法を使用して部分的に暗号化され `F4VDRMParameters.setVideoEncryptionLevel`ます。

Java APIを使用してFLVまたはF4Vファイルを暗号化するには、次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内の開発環境の設定」で説明されているすべてのJARファイルを含めます。
1. 署名に必要な `ServerCredential` 資格情報を読み込むためのインスタンスを作成します。
1. インスタンスを作 `MediaEncrypter` 成します。 ファイルの種 `MediaEncryperFactory` 類がわからない場合は、を使用します。 それ以外の場合は、またはを直接 `FLVEncrypter` 作成で `F4VEncrypter` きます。
1. オブジェクトを使用して暗号化オプションを指 `DRMParameters` 定します。
1. オブジェクトを使用して署名オプションを `SignatureParameters` 設定し、そのインスタ `ServerCredential` ンスをメソッドに渡 `setServerCredentials` します。
1. オブジェクトを使用してキーとライセンス情報を設 `V2KeyParameters` 定します。 方法を使用してポリシーを設定 `setPolicies` します。 およびメソッドを呼び出して、クライアントがライセンスサーバーに接続するために必要な情報 `setLicenseServerUrl` を設定 `setLicenseServerTransportCertificate` します。 この方法を使用してCEK暗号化オプションを設定し、 `setKeyProtectionOptions` この方法を使用してそのカスタムプロパティを設定 `setCustomProperties` します。 最後に、使用する暗号化の種類に応じて、オブジェクトを、、、ま `DRMKeyParameters` たはのいずれかにキャストし、 `VideoDRMParameters`暗 `AudioDRMParameters`号化オ `FLVDRMParameters`プシ `F4VDRMParameters`ョンを設定します。
1. このメソッドに入力ファイルと出力ファイルと暗号化オプションを渡して、コンテンツを暗号化 `MediaEncrypter.encryptContent` します。

コンテンツの暗号化方法を示すサンプルコードについては、リファレンス `com.adobe.flashaccess.samples.mediapackager.EncryptContent` 実装のコマンドラインツールの「samples」ディレクトリを参照してください。
