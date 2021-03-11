---
description: Primetime DRMを設定する場合は、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 また、IncorporatedのAdobe Systemsに証明書を要求する必要があります。 次に、Adobeは、パッケージ化されたコンテンツ、ライセンス、およびクライアントとサーバー間の通信の整合性を保護するために使用する複数の資格情報を発行します。
title: 開発環境のセットアップ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# 開発環境のセットアップ{#set-up-your-development-environment}

Primetime DRMを設定する場合は、DVDからファイルをコピーします。 これらのファイルには、コード、証明書、およびサードパーティクラスを含むJARファイルが含まれます。 また、IncorporatedのAdobe Systemsに証明書を要求する必要があります。 次に、Adobeは、パッケージ化されたコンテンツ、ライセンス、およびクライアントとサーバー間の通信の整合性を保護するために使用する複数の資格情報を発行します。

Adobeは、DVDでPrimetime DRM SDKを提供します。

1. [!DNL [DRM DVD]/SDK/]から開発システム（Javaクラスパス上）に次のファイルをコピーします。

   * [!DNL adobe-flashaccess-certs.jar] -Adobeルート証明書を含みます。
   * [!DNL adobe-flashaccess-sdk.jar] - Primetime DRMコアSDKクラスを含みます
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Primetime DRM Professional SDKクラスが含まれます。これはProfessional機能にのみ必要です

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

1. （オプション）パフォーマンスを向上させるために、適切なプラットフォーム固有のライブラリを[!DNL [DRM DVD]/SDK/thirdparty/cryptoj/]から開発システムにコピーして、暗号化操作のネイティブサポートを有効にできます（パスに場所を忘れない）。

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

      >[!NOTE]
      >
      >これらのライブラリの32ビット版と64ビット版が提供されています。 64ビット版のOSを使用し、64ビット版のJavaを実行している場合は、64ビット版のみを使用してください。

1. （オプション）AdobeFlashメディアRights Managementサーバー(FMRMS)1.xとの互換性に関連する機能については、開発システムに`[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]`をコピーします。

   これは、以前にFMRMS 1.xをデプロイしたが、FMRMSで保護されたコンテンツを再パッケージ化したくない場合にのみ展開してください。 この場合、古いコンテンツやクライアントを管理できるように、このサポートをライセンスサーバに追加する必要があります。
