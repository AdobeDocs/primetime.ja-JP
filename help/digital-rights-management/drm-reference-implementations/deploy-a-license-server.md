---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーのデプロイ
title: ライセンスサーバーのデプロイ
uuid: bee7ead1-ed13-4894-80f9-5196bf2f818f
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# ライセンスサーバーのデプロイ{#deploy-the-license-server}

1. 参照実装のwarファイルを、Tomcatサーバー上の `webapps` ディレクトリにコピーします。

   参照実装ライセンスサーバーをそのまま使用するには、ライセンスサーバーのWARファイル( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`)をTomcatサーバー上の `webapps` ディレクトリにコピーします。

   参照実装ライセンスサーバーをカスタマイズする場合は、作成元のサーバーwarファイルを `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars``webapps` ディレクトリにコピーします。

   >[!NOTE]
   >
   >ライセンスサーバーのWARファイルを以前にデプロイした場合は、Tomcatサーバーのディレクトリ内にある展開済みのWAR [!DNL webapps] ディレクトリを削除する必要がある場合があります。
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >FlashメディアRights Management(FMRMS)v1.5コンテンツとの後方互換性が必要な場合を除き、デプロイしないでください。 [!DNL edsws.war] （これは非常にまれな要件です。）
   >
   >WARファイルの開梱をTomcatで禁止する場合は、 `server.xml` ディレクトリ `conf` でを編集し、に設定 `unpackWARs` し `false`ます。

1. ディレクトリの内容全体をディレクトリ `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` にコピーし [!DNL tomcat] ます。

   この [!DNL resources] ディレクトリには、次のものが含まれます。

   * [!DNL flashaccesstools.properties]  — ライセンスサーバーのプロパティファイル。
   * [!DNL log4j.xml]  — ライセンスサーバーログの設定
   * [!DNL *.pol] - DRMポリシーファイルのサンプル。

   また、Adobe証明書ファイルをこの場所にコピーすることもできます。

1. でライセンスサーバの設定を変更 [!DNL flashaccesstools.properties] して、サーバの設定を反映します。

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

1. Tomcat `catalina.properties``conf` ディレクトリ内のファイルを編集します。ディレクトリの場所（または、プロパティファイルと他のリソースファイルを保存した別の場所）を [!DNL resources]`shared.loader` プロパティに追加します。

   たとえば、[!DNL `flashaccess-refimpl.properties` Tomcat home []\resources\]にある場合は、次のように指定します。

   ```
   shared.loader=..\resources
   ```

   これはクラスパス `flashaccess-refimpl.properties` に配置されます。
1. その他のリソースファイル( [!DNL log4j.xml]、ポリシーファイル、証明書)がディレクトリ内にあるか、または [!DNL resources] クラスパス上に存在し、で指定した場所にあることを確認 [!DNL flashaccess-refimpl.properties]します。

   最初はデバッグモードで実行す `log4j` る必要がある場合があります。 で、 [!DNL log4j.xml]true `debug` に設定します。

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Tomcat [!DNL bin] ディレクトリから、サーバーを開始します。

   Linuxの場合：

   ```
   catalina.sh start
   ```

   Windowsの場合：

   ```
   catalina.bat start
   ```
