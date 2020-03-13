---
seo-title: コンテンツの暗号化
title: コンテンツの暗号化
uuid: 03f33473-bcd4-4e06-a823-e944897cb28e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コンテンツの暗号化{#encrypting-content}

ビデオコンテンツは、オブジェクトを使用して暗号 `MediaEncrypter` 化します。 オーディオトラックのみを含むメディアファイルを暗号化できます。 部分的な暗号化のみを適用することもできます。例えば、ローエンドデバイス用にH.264コンテンツを暗号化する場合のパフォーマンスを向上させます。

Java APIを使用してメディアファイルを暗号化するには：

1. 開発環境を設定し、「プロジェクト内の開発環境の設定」に記載されてい *るすべてのJARファイルを* 含めます。
1. 署名に必要な `ServerCredential` 資格情報を読み込むためのインスタンスを作成します。
1. インスタンスを作 `MediaEncrypter` 成します。 ファイルの種 `MediaEncryperFactory` 類がわからない場合は、を使用します。

1. オブジェクトを使用して暗号化オプションを指 `DRMParameters` 定します。
1. オブジェクトを使用して署名オプションを `SignatureParameters` 設定し、そのインスタ `ServerCredential` ンスをメソッドに渡 `setServerCredentials` します。

1. オブジェクトを使用してキーとライセンス情報を設 `V2KeyParameters` 定します。 方法を使用してDRMポリシーを設定 `setPolicies` します。 およびメソッドを呼び出して、クライアントがライセンスサーバーに接続するために必要な情報 `setLicenseServerUrl` を設定 `setLicenseServerTransportCertificate` します。 この方法を使用してCEK暗号化オプションを設定し、 `setKeyProtectionOptions` この方法を使用してそのカスタムプロパティを設定 `setCustomProperties` します。 最後に、使用する暗号化の種類に応じて、オブジェクトを適 `DRMKeyParameters` 切な種類(、 `VideoDRMParameters``AudioDRMParameters`)にキャストし、暗号化オプションを設定します。

1. このメソッドに入力ファイルと出力ファイルと暗号化オプションを渡して、コンテンツを暗号化 `MediaEncrypter.encryptContent` します。

コンテンツの暗号化方法を示すサンプルコードについては、リファレンス実装 `com.adobe.flashaccess.samples.mediapackager.EncryptContent` のコマンドラインツールディレクトリのを参照して [!DNL samples/] ください。
