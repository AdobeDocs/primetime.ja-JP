---
description: Primetime DRMを設定する場合は、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 さらに、Adobe Systems, Incorporatedから証明書を要求する必要があります。 その後、アドビから複数の資格情報が発行され、パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用されます。
seo-description: Primetime DRMを設定する場合は、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 さらに、Adobe Systems, Incorporatedから証明書を要求する必要があります。 その後、アドビから複数の資格情報が発行され、パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用されます。
seo-title: 開発環境の設定
title: 開発環境の設定
uuid: 68afefe8-7ec6-466e-89a8-bc0da8afb4c8
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# 開発環境の設定 {#set-up-your-development-environment}

Primetime DRMを設定する場合は、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 さらに、Adobe Systems, Incorporatedから証明書を要求する必要があります。 その後、アドビから複数の資格情報が発行され、パッケージ化されたコンテンツ、ライセンス、クライアントとサーバー間の通信の整合性を保護するために使用されます。

アドビは、DVDでPrimetime DRM SDKを提供しています。

1. [!DNL [DRM DVD]/SDK/]から開発システム（Javaクラスパス上）に次のファイルをコピーします。

   * [!DNL adobe-flashaccess-certs.jar]  — アドビのルート証明書を含む
   * [!DNL adobe-flashaccess-sdk.jar] - Primetime DRMコアSDKクラスを含む
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Primetime DRM Professional SDKクラスを含み、Professional機能にのみ必要

1. [!DNL [DRM DVD]/SDK/thirdparty]から開発システムに次のファイルをコピーします。

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

1. （オプション）パフォーマンスを向上させるには、適切なプラットフォーム固有のライブラリを[!DNL [DRM DVD]/SDK/thirdparty/cryptoj/]から開発システムにコピーして、暗号化操作のネイティブサポートを有効にします（パスに場所を入れておくことを忘れない）。

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

      >[!NOTE]
      >
      >これらのライブラリの32ビット版と64ビット版が用意されています。 64ビット版のOSを使用し、64ビット版のJavaを実行している場合は、64ビット版のみを使用してください。

1. （オプション）Adobe Flash Media Rights Management Server(FMRMS)1.xとの互換性に関する機能については、開発システム `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` に次のコピーを作成します。

   これは、以前にFMRMS 1.xをデプロイし、FMRMSで保護されたコンテンツを再パッケージ化しない場合にのみ展開します。 この場合、古いコンテンツやクライアントを管理できるように、このサポートをライセンスサーバーに追加する必要があります。
