---
description: Adobe「® Access™」を使用するように設定するには、DVD からファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含む JAR ファイルが含まれます。 さらに、Adobe Systems Incorporatedに証明書を要求します。 パッケージ化されたコンテンツ、ライセンス、クライアントとサーバ間の通信の整合性を保護するために使用される複数の資格情報が発行されます。
title: 開発環境の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# SDK の設定 {#setting-up-the-sdk}

Adobe「® Access™」を使用するように設定するには、DVD からファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含む JAR ファイルが含まれます。 さらに、Adobe Systems Incorporatedに証明書を要求します。 パッケージ化されたコンテンツ、ライセンス、クライアントとサーバ間の通信の整合性を保護するために使用される複数の資格情報が発行されます。

Adobeアクセス SDK は、次の 2 種類で使用できます。
* Adobe Access Core SDK
* Adobe Access Professional SDK

次の表に、Adobeアクセス SDK の基本的な比較を示します。

| 機能 | Adobe Access Core SDK | Adobe Access Professional SDK |
|---|---|---|
| Flash Access2.0 の機能 | 利用可能 | 利用可能 |
| キーの回転 | - | 利用可能 |
| ドメインサポート | 利用可能 | 利用可能 |
| 拡張ライセンスチェーニング | 利用可能 | 利用可能 |
| 同期メッセージ | 利用可能 | 利用可能 |
| ライセンスの事前生成 | 利用可能 | 利用可能 |
| 埋め込みライセンス | 利用可能 | 利用可能 |

## 開発環境の設定 {#setting-up-the-development-environment}

DVD から、開発環境で使用する次の SDK ファイルと Java クラスパスをコピーします。

* adobe-flashaccess-certs.jar(Adobeのルート証明書を含む )
* adobe-flashaccess-sdk.jar(Adobe Access Core SDK クラスを含む )
* adobe-flashaccess-sdk-pro.jar(Adobe Access Professional SDK クラスを含み、Professional 機能にのみ必要 )

SDK の「thirdparty」フォルダーの DVD にも、次のサードパーティの JAR ファイルが必要です。

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

パフォーマンスを向上させるには、SDK の「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイして、暗号化操作のネイティブサポートをオプションで有効にできます。 ネイティブサポートを有効にするには、プラットフォーム用のライブラリ（Windows の場合は jsafe.dll 、Linux の場合は libjsafe.so ）をパスに追加します。 これらのライブラリの 32 ビット版と 64 ビット版が提供されています。 （64 ビットバージョンは、64 ビット OS を使用していて、64 ビットバージョンの Java を実行している場合にのみ使用してください）。

さらに、SDK のオプションの部分は adobe-flashaccess-lcrm.jar です。 このファイルは、AdobeFlashメディアRights Managementサーバー (FMRMS)1.x の互換性に関連する機能にのみ必要です。 以前に FMRMS 1.x をデプロイし、FMRMS で保護されたコンテンツを再パッケージ化したくない場合は、古いコンテンツやクライアントを処理できるように、ライセンスサーバーにサポートを追加する必要があります。
