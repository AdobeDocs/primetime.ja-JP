---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーのデプロイ
title: ライセンスサーバーのデプロイ
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 29149594c4b41956a091ef27093304e74ff15f2f

---


# ライセンスサーバーのデプロイ{#deploy-the-license-server}

1. 参照実装のwarファイルをTomcatサーバー上のデ `webapps` ィレクトリにコピーします。

   参照実装ライセンスサーバーをそのまま使用するには、ライセンスサーバーのWARファイル( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`)をTomcatサーバー上のデ `webapps` ィレクトリにコピーします。

   参照実装ライセンスサーバーをカスタマイズする場合は、作成元のサーバーのwarファイルをディレクトリ `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` にコピー `webapps` します。

   >[!NOTE]
   >
   >以前にライセンスサーバーのWARファイルをデプロイした場合は、Tomcatサーバー上のディレクトリ内の展開済みのWARディレク [!DNL webapps] トリを削除する必要があります。       >
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >Flash Media Rights Management(FMRMS)v1.5 [!DNL edsws.war] コンテンツとの下位互換性が必要な場合を除き、デプロイしないでください。 （これは非常にまれな要件です）。
   >
   >TomcatでWARファイルの展開を禁止する場合は、ディレクトリ内のを編集し、 `server.xml` をに設定 `conf` する必要があ `unpackWARs` ります `false`。

1. ディレクトリの内容全体をディレ `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` クトリにコピー [!DNL tomcat] します。

   このディレク [!DNL resources] トリには、

   * [!DNL flashaccesstools.properties]  — ライセンスサーバーのプロパティファイル。
   * [!DNL log4j.xml]  — ライセンスサーバーログの設定
   * [!DNL *.pol] - DRMポリシーファイルの例。
   また、アドビ認証ファイルをこの場所にコピーすることもできます。

1. でライセンスサーバの設定を変更し、 [!DNL flashaccesstools.properties] サーバの設定を反映させます。

   少なくとも、次のプロパティの値を設定します。

   * `config.resourcesDirectory`
   * `HandlerConfiguration.ServerTransportCredential`
   * `HandlerConfiguration.ServerTransportCredential.password`
   * `LicenseHandler.ServerCredential`
   * `LicenseHandler.ServerCredential.password`
   * `MetaDataConverter.SignatureParameters.ServerCredential`
   * `MetaDataConverter.SignatureParameters.ServerCredential.password`
   * `V2KeyParameters.LicenseServerUrl`
   * `V2KeyParameters.KeyOptions.AsymmetricKeyOptions.Certificate`
   * V2KeyParameters.LicenseServerTransportCertificate

1. Tomcatディレクトリ `catalina.properties` 内のファイルを編集 `conf` します。ディレクトリの場所(ま [!DNL resources] たはプロパティファイルと他のリソースファイルを保存した別の場所)をプロパティに追加し `shared.loader` ます。

   たとえば、[!DNL `flashaccess-refimpl.properties` Tomcat home []\resources\]に

   ```
   shared.loader=..\resources
   ```

   これはクラスパ `flashaccess-refimpl.properties` スに配置されます。
1. 他のリソースファイル(、ポリシーフ [!DNL log4j.xml]ァイル、証明書)がディレクトリ内にあるか、またはクラスパス上にあ [!DNL resources] り、で指定した場所にあることを確認しま [!DNL flashaccess-refimpl.properties]す。

   最初はデバッグモードで実行する `log4j` 必要があります。 で、 [!DNL log4j.xml]trueに設 `debug` 定します。

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Tomcatディレクトリ [!DNL bin] から、サーバーを起動します。

   Linuxの場合：

   ```
   catalina.sh start
   ```

   Windowsの場合：

   ```
   catalina.bat start
   ```
