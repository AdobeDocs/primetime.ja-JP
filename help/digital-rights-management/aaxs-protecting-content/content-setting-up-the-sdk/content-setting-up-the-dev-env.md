---
description: Adobe® Access™を使用するように設定するには、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 また、Adobe Systems Incorporatedに証明書を要求する。 パッケージ化されたコンテンツ、ライセンス、およびクライアントとサーバー間の通信の整合性を保護するために使用される複数の資格情報が発行されます。
title: 開発環境の設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# SDKのセットアップ{#setting-up-the-sdk}

Adobe® Access™を使用するように設定するには、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 また、Adobe Systems Incorporatedに証明書を要求する。 パッケージ化されたコンテンツ、ライセンス、およびクライアントとサーバー間の通信の整合性を保護するために使用される複数の資格情報が発行されます。

AdobeアクセスSDKは、次の2種類があります。
* Adobe Access CoreSDK
* Adobe Access ProfessionalSDK

次の表に、AdobeアクセスSDKの基本的な比較を示します。

| 機能 | Adobe Access CoreSDK | Adobe Access ProfessionalSDK |
|---|---|---|
| Flash Access2.0の機能 | 利用可能 | 利用可能 |
| キーの回転 | - | 利用可能 |
| ドメインのサポート | 利用可能 | 利用可能 |
| 拡張ライセンスチェーン | 利用可能 | 利用可能 |
| 同期メッセージ | 利用可能 | 利用可能 |
| ライセンスの事前生成 | 利用可能 | 利用可能 |
| 埋め込みライセンス | 利用可能 | 利用可能 |

## 開発環境の設定{#setting-up-the-development-environment}

DVDから、開発環境とJavaクラスパスで使用する次のSDKファイルをコピーします。

* adobe-flashaccess-certs.jar(Adobeルート証明書を含む)
* adobe-flashaccess-sdk.jar(Adobe Access CoreSDKクラスを含む)
* adobe-flashaccess-sdk-pro.jar(Adobe Access ProfessionalSDKクラスを含む。Professional機能にのみ必要)

次のサードパーティJARファイルも、SDKの「サードパーティ」フォルダー内のDVDに含まれている必要があります。

* bcmail-jdk15-141.jar
* bcprov-jdk15-141.jar
* commons-discovery-0.4.jar
* commons-logging-1.1.1.jar
* cryptoj.jar
* jaxb-api.jar
* jaxb-impl.jar
* jaxb-libs.jar
* relaxngDatatype.jar
* rm-pdrl.jar
* xsdlib.jar

パフォーマンスを向上させるために、SDKの「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイすることで、暗号化操作のネイティブサポートをオプションで有効にできます。 ネイティブサポートを有効にするには、プラットフォーム用のライブラリ（Windowsの場合はjsafe.dll、Linuxの場合はlibjsafe.so）をパスに追加します。 これらのライブラリの32ビット版と64ビット版が提供されています。 （64ビット版は、64ビット版のOSを使用し、64ビット版のJavaを実行している場合にのみ使用する必要があります）。

また、SDKのオプションの部分はadobe-flashaccess-lcrm.jarです。 このファイルは、AdobeFlashメディアRights Managementサーバー(FMRMS)1.xの互換性に関連する機能にのみ必要です。 以前にFMRMS 1.xをデプロイしておき、FMRMSで保護されたコンテンツを再パッケージ化したくない場合は、古いコンテンツとクライアントを処理できるように、ライセンスサーバーにサポートを追加する必要があります。
