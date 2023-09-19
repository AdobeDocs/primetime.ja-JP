---
title: コンテンツの暗号化
description: コンテンツの暗号化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# コンテンツの暗号化{#encrypting-content}

ビデオコンテンツを `MediaEncrypter` オブジェクト。 オーディオトラックのみを含むメディアファイルを暗号化できます。 また、部分的な暗号化のみを適用できます。例えば、ロワーエンドデバイス用に H.264 コンテンツを暗号化する場合のパフォーマンスを向上させます。

Java API を使用してメディアファイルを暗号化するには：

1. 開発環境を設定し、 *開発環境の設定* を選択します。
1. の作成 `ServerCredential` 署名に必要な資格情報を読み込むためのインスタンスです。
1. の作成 `MediaEncrypter` インスタンス。 の使用 `MediaEncryperFactory` ファイルの種類がわからない場合は、

1. を使用して暗号化オプションを指定します。 `DRMParameters` オブジェクト。
1. 以下を使用して署名オプションを設定します： `SignatureParameters` オブジェクトを選択し、 `ServerCredential` インスタンスを `setServerCredentials` メソッド。

1. キーとライセンス情報を、 `V2KeyParameters` オブジェクト。 を使用して DRM ポリシーを設定する `setPolicies` メソッド。 クライアントがライセンスサーバーに接続するために必要な情報を設定するには、 `setLicenseServerUrl` および `setLicenseServerTransportCertificate` メソッド。 CEK 暗号化オプションを設定するには、 `setKeyProtectionOptions` メソッド、および `setCustomProperties` メソッド。 最後に、使用する暗号化の種類に応じて、 `DRMKeyParameters` オブジェクトを適切な型 ( `VideoDRMParameters`, `AudioDRMParameters`) をクリックし、暗号化オプションを設定します。

1. に入力ファイルと出力ファイルおよび暗号化オプションを渡すことで、コンテンツを暗号化します `MediaEncrypter.encryptContent` メソッド。

コンテンツの暗号化方法を示すサンプルコードについては、 `com.adobe.flashaccess.samples.mediapackager.EncryptContent` （「参照実装」コマンドラインツール） [!DNL samples/] ディレクトリ。
