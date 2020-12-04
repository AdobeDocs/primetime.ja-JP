---
seo-title: コンテンツの暗号化
title: コンテンツの暗号化
uuid: 03f33473-bcd4-4e06-a823-e944897cb28e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# コンテンツの暗号化{#encrypting-content}

ビデオコンテンツは`MediaEncrypter`オブジェクトを使用して暗号化します。 オーディオトラックのみを含むメディアファイルを暗号化できます。 部分的な暗号化のみを適用することもできます。例えば、ローエンドデバイス用にH.264コンテンツを暗号化する場合のパフォーマンスを向上させるために使用します。

Java APIを使用してメディアファイルを暗号化するには：

1. 開発環境を設定し、プロジェクト内の&#x200B;*開発環境の設定*&#x200B;で説明されているすべてのJARファイルを含めます。
1. `ServerCredential`インスタンスを作成して、署名に必要な資格情報を読み込みます。
1. `MediaEncrypter`インスタンスを作成します。 ファイルの種類がわからない場合は、`MediaEncryperFactory`を使用します。

1. `DRMParameters`オブジェクトを使用して暗号化オプションを指定します。
1. `SignatureParameters`オブジェクトを使用して署名オプションを設定し、`ServerCredential`インスタンスを`setServerCredentials`メソッドに渡します。

1. `V2KeyParameters`オブジェクトを使用して、キーとライセンスの情報を設定します。 `setPolicies`メソッドを使用してDRMポリシーを設定します。 `setLicenseServerUrl`メソッドと`setLicenseServerTransportCertificate`メソッドを呼び出して、クライアントがライセンスサーバーに接続するために必要な情報を設定します。 `setKeyProtectionOptions`メソッドを使用してCEK暗号化オプションを設定し、`setCustomProperties`メソッドを使用してそのカスタムプロパティを設定します。 最後に、使用する暗号化の種類に応じて、`DRMKeyParameters`オブジェクトを適切な種類(`VideoDRMParameters`、`AudioDRMParameters`)にキャストし、暗号化オプションを設定します。

1. 入力ファイルと出力ファイル、および暗号化オプションを`MediaEncrypter.encryptContent`メソッドに渡して、コンテンツを暗号化します。

コンテンツの暗号化方法を示すサンプルコードについては、リファレンス実装のコマンドラインツール[!DNL samples/]ディレクトリの`com.adobe.flashaccess.samples.mediapackager.EncryptContent`を参照してください。
