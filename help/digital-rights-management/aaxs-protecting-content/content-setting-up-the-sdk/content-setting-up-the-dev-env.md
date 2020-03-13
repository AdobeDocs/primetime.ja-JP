---
description: Adobe® Access™を使用するように設定するには、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 さらに、Adobe Systems Incorporatedから証明書を要求します。 パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用される複数の資格情報が発行されます。
seo-description: Adobe® Access™を使用するように設定するには、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 さらに、Adobe Systems Incorporatedから証明書を要求します。 パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用される複数の資格情報が発行されます。
seo-title: 開発環境の設定
title: 開発環境の設定
uuid: 1f192783-9c9a-4342-909a-4881248a85ad
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# SDKの設定 {#setting-up-the-sdk}

Adobe® Access™を使用するように設定するには、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 さらに、Adobe Systems Incorporatedから証明書を要求します。 パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用される複数の資格情報が発行されます。

Adobe Access SDKは、次の2種類で使用できます。
* Adobe Access Core SDK
* Adobe Access Professional SDK

次の表に、Adobe Access SDKの基本的な比較を示します。

| 機能 | Adobe Access Core SDK | Adobe Access Professional SDK |
|---|---|---|
| Flash Access 2.0の機能 | 使用可能 | 使用可能 |
| キーの回転 | - | 使用可能 |
| ドメインのサポート | 使用可能 | 使用可能 |
| 拡張ライセンスチェーン | 使用可能 | 使用可能 |
| 同期メッセージ | 使用可能 | 使用可能 |
| ライセンスの事前生成 | 使用可能 | 使用可能 |
| 埋め込みライセンス | 使用可能 | 使用可能 |

## 開発環境の設定 {#setting-up-the-development-environment}

DVDから、開発環境とJavaクラスパスで使用する次のSDKファイルをコピーします。

* adobe-flashaccess-certs.jar（Adobeルート証明書を含む）
* adobe-flashaccess-sdk.jar（Adobe Access Core SDKクラスを含む）
* adobe-flashaccess-sdk-pro.jar（Adobe Access Professional SDKクラスを含み、Professional機能にのみ必要）

次のサードパーティJARファイルも、SDKの「thirdparty」フォルダー内のDVDに保存する必要があります。

* bcmail-jdk15-141.jar
* bcprov-jdk15-141.jar
* commons-discovery-0.4.jar
* commons-logging-1.1.1.jar
* cryptoj.jar
* jaxb-api.jar
* jaxb-impl.jar
* jaxb-libs.jar
* relaxingDatatype.jar
* rm-pdrl.jar
* xsdlib.jar

パフォーマンスを向上させるために、SDKの「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイすることで、オプションで暗号化操作のネイティブサポートを有効にできます。 ネイティブサポートを有効にするには、プラットフォームのライブラリ（Windowsの場合はjsafe.dll、Linuxの場合はlibjsafe.so）をパスに追加します。 これらのライブラリの32ビット版と64ビット版が提供されています。 （64ビット版は、64ビット版のOSを使用し、64ビット版のJavaを実行している場合にのみ使用する必要があります）。

また、SDKのオプションの部分はadobe-flashaccess-lcrm.jarです。 このファイルは、Adobe Flash Media Rights Management Server(FMRMS)1.xの互換性に関連する機能にのみ必要です。 以前にFMRMS 1.xをデプロイしており、FMRMSで保護されたコンテンツを再パッケージ化したくない場合は、古いコンテンツやクライアントを処理できるように、ライセンスサーバーにサポートを追加する必要があります。
