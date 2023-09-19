---
description: Primetime DRM を設定する場合は、DVD からファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含む JAR ファイルが含まれます。 さらに、Incorporated(Adobe Systems) に証明書を要求する必要があります。 Adobeは、パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用する複数の資格情報を発行します。
title: 開発環境の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 開発環境の設定 {#set-up-your-development-environment}

Primetime DRM を設定する場合は、DVD からファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含む JAR ファイルが含まれます。 さらに、Incorporated(Adobe Systems) に証明書を要求する必要があります。 Adobeは、パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用する複数の資格情報を発行します。

Adobeは、DVD に Primetime DRM SDK を提供します。

1. 次のファイルを [!DNL [DRM DVD]/SDK/] を（Java クラスパス上の）開発システムに追加します。

   * [!DNL adobe-flashaccess-certs.jar] -Adobeルート証明書を含む
   * [!DNL adobe-flashaccess-sdk.jar] - Primetime DRM コア SDK クラスを含む
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Primetime DRM Professional SDK クラスが含まれ、Professional 機能にのみ必要です

1. 次のファイルを [!DNL [DRM DVD]/SDK/thirdparty] を開発システムに追加します。

   * [!DNL bcmail-jdk15-141.jar]
   * [!DNL bcprov-jdk15-141.jar]
   * [!DNL commons-discovery-0.4.jar]
   * [!DNL commons-logging-1.1.1.jar]
   * [!DNL cryptoj.jar]
   * [!DNL jaxb-api.jar]
   * [!DNL jaxb-impl.jar]
   * [!DNL jaxb-libs.jar]
   * [!DNL relaxngDatatype.jar]
   * [!DNL rm-pdrl.jar]
   * [!DNL xsdlib.jar]
   * [!DNL jackson-annotations-2.4.0-rc4-20140522.175222-3.jar]
   * [!DNL jackson-core--2.4.0-rc4-20140529.184520-13.jar]
   * [!DNL jackson-databind-2.4.0-rc4-20140603.005043-38.jar]

1. （オプション）パフォーマンスを向上させるために、[!DNL [DRM DVD]/SDK/thirdparty/cryptoj/] を開発システムに追加します（パスに場所を忘れずに配置してください）。

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

     >[!NOTE]
     >
     >これらのライブラリの 32 ビット版と 64 ビット版を利用できます。 64 ビット版の Java を実行している 64 ビット版の OS がある場合にのみ、64 ビット版を使用してください。

1. （オプション）AdobeFlashメディアRights Managementサーバー (FMRMS)1.x の互換性に関連する機能については、 `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` を開発システムに追加します。

   これは、以前に FMRMS 1.x をデプロイし、FMRMS で保護されたコンテンツを再パッケージ化しない場合にのみデプロイします。 この場合、古いコンテンツやクライアントを管理できるよう、ライセンスサーバーにこのサポートを追加する必要があります。
