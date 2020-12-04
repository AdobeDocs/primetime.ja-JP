---
seo-title: コンテンツの暗号化
title: コンテンツの暗号化
uuid: ea71154e-557b-447e-bc14-208232f00be1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# コンテンツの暗号化{#encrypting-content}

FLVとF4Vコンテンツの暗号化には、`MediaEncrypter`オブジェクトの使用が含まれます。 オーディオトラックのみを含むFLVとF4Vファイルをパッケージ化することもできます。 ローエンドデバイス用にH.264コンテンツを暗号化する場合、パフォーマンスを向上させるために部分的な暗号化のみを適用すると効果的です。 このような場合、F4Vファイルは、`F4VDRMParameters.setVideoEncryptionLevel`メソッドを使用して部分的に暗号化できます。

Java APIを使用してFLVまたはF4Vファイルを暗号化するには、次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内での開発環境の設定」に記載されているすべてのJARファイルを含めます。
1. `ServerCredential`インスタンスを作成して、署名に必要な資格情報を読み込みます。
1. `MediaEncrypter`インスタンスを作成します。 ファイルの種類がわからない場合は、`MediaEncryperFactory`を使用します。 それ以外の場合は、`FLVEncrypter`または`F4VEncrypter`を直接作成できます。
1. `DRMParameters`オブジェクトを使用して暗号化オプションを指定します。
1. `SignatureParameters`オブジェクトを使用して署名オプションを設定し、`ServerCredential`インスタンスを`setServerCredentials`メソッドに渡します。
1. `V2KeyParameters`オブジェクトを使用して、キーとライセンスの情報を設定します。 `setPolicies`メソッドを使用してポリシーを設定します。 `setLicenseServerUrl`メソッドと`setLicenseServerTransportCertificate`メソッドを呼び出して、クライアントがライセンスサーバーに接続するために必要な情報を設定します。 `setKeyProtectionOptions`メソッドを使用してCEK暗号化オプションを設定し、`setCustomProperties`メソッドを使用してそのカスタムプロパティを設定します。 最後に、使用する暗号化の種類に応じて、`DRMKeyParameters`オブジェクトを`VideoDRMParameters`、`AudioDRMParameters`、`FLVDRMParameters`、または`F4VDRMParameters`のいずれかにキャストし、暗号化オプションを設定します。
1. 入力ファイルと出力ファイル、および暗号化オプションを`MediaEncrypter.encryptContent`メソッドに渡して、コンテンツを暗号化します。

コンテンツの暗号化方法を示すサンプルコードについては、リファレンス実装のコマンドラインツールの「samples」ディレクトリの`com.adobe.flashaccess.samples.mediapackager.EncryptContent`を参照してください。
