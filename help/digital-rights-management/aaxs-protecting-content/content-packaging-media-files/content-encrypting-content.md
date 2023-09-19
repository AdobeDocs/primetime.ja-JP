---
title: コンテンツの暗号化
description: コンテンツの暗号化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# コンテンツの暗号化{#encrypting-content}

FLV および F4V コンテンツの暗号化には、 `MediaEncrypter` オブジェクト。 オーディオトラックのみを含む FLV および F4V ファイルをパッケージ化することもできます。 ロワーエンドデバイス用に H.264 コンテンツを暗号化する場合、パフォーマンスを向上させるために部分的な暗号化のみを適用するのが実用的な場合があります。 このような場合、F4V ファイルは、 `F4VDRMParameters.setVideoEncryptionLevel`メソッド。

Java API を使用して FLV または F4V ファイルを暗号化するには、次の手順を実行します。

1. 開発環境を設定し、プロジェクト内での開発環境の設定で説明されているすべての JAR ファイルを含めます。
1. の作成 `ServerCredential` 署名に必要な資格情報を読み込むためのインスタンスです。
1. の作成 `MediaEncrypter` インスタンス。 の使用 `MediaEncryperFactory` ファイルの種類がわからない場合は、 それ以外の場合は、 `FLVEncrypter` または `F4VEncrypter` を直接使用します。
1. を使用して暗号化オプションを指定します。 `DRMParameters` オブジェクト。
1. 以下を使用して署名オプションを設定します： `SignatureParameters` オブジェクトを選択し、 `ServerCredential` インスタンスを `setServerCredentials` メソッド。
1. キーとライセンス情報を、 `V2KeyParameters` オブジェクト。 を使用したポリシーの設定 `setPolicies` メソッド。 クライアントがライセンスサーバーに接続するために必要な情報を設定するには、 `setLicenseServerUrl` および `setLicenseServerTransportCertificate` メソッド。 CEK 暗号化オプションを設定するには、 `setKeyProtectionOptions` メソッド、および `setCustomProperties` メソッド。 最後に、使用する暗号化の種類に応じて、 `DRMKeyParameters` 次のいずれかに対して異議を唱える `VideoDRMParameters`, `AudioDRMParameters`, `FLVDRMParameters`または `F4VDRMParameters`をクリックし、暗号化オプションを設定します。
1. に入力ファイルと出力ファイルおよび暗号化オプションを渡すことで、コンテンツを暗号化します `MediaEncrypter.encryptContent` メソッド。

コンテンツを暗号化する方法を示すサンプルコードについては、 `com.adobe.flashaccess.samples.mediapackager.EncryptContent` 「リファレンス実装」コマンドラインツールの「samples」ディレクトリ。
