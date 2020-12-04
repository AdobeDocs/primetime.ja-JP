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


# ライセンスサーバー{#deploy-the-license-server}を展開します

1. 参照実装のwarファイルを、Tomcatサーバーの`webapps`ディレクトリにコピーします。

   参照実装ライセンスサーバーをそのまま使用するには、ライセンスサーバーのWARファイル(`[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`)をTomcatサーバーの`webapps`ディレクトリにコピーします。

   参照実装のライセンスサーバーをカスタマイズする場合は、`DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars`から作成したサーバーwarファイルを`webapps`ディレクトリにコピーします。

   >[!NOTE]
   >
   >ライセンスサーバーのWARファイルを以前にデプロイした場合は、Tomcatサーバーの[!DNL webapps]ディレクトリ内の展開済みのWARディレクトリを削除する必要がある場合があります。
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]


   >[!NOTE]
   >
   >FlashメディアRights Management(FMRMS)v1.5コンテンツとの下位互換性が必要な場合を除き、[!DNL edsws.war]をデプロイしないでください。 （これは非常にまれな要件です。）
   >
   >TomcatがWARファイルを開くのを防ぐには、`conf`ディレクトリの`server.xml`を編集し、`unpackWARs`を`false`に設定します。

1. `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\`ディレクトリの内容を[!DNL tomcat]ディレクトリにコピーします。

   [!DNL resources]ディレクトリには、次のものが含まれます。

   * [!DNL flashaccesstools.properties]  — ライセンスサーバーのプロパティファイル。
   * [!DNL log4j.xml]  — ライセンスサーバーログの設定
   * [!DNL *.pol] - DRMポリシーファイルのサンプル。

   また、Adobe証明書ファイルをこの場所にコピーすることもできます。

1. [!DNL flashaccesstools.properties]のライセンスサーバー設定を変更して、サーバー設定を反映します。

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

1. Tomcat `conf`ディレクトリ内の`catalina.properties`ファイルを編集します。[!DNL resources]ディレクトリの場所（または、プロパティファイルや他のリソースファイルを保存した別の場所）を`shared.loader`プロパティに追加します。

   例えば、`flashaccess-refimpl.properties`が[!DNL [Tomcat home]\resources\]にある場合、次のように指定します。

   ```
   shared.loader=..\resources
   ```

   これは`flashaccess-refimpl.properties`をクラスパスに配置します。
1. その他のリソースファイル（[!DNL log4j.xml]、ポリシーファイル、証明書）が[!DNL resources]ディレクトリ内にあるか、または[!DNL flashaccess-refimpl.properties]で指定されたクラスパスとその場所にあることを確認してください。

   `log4j`は、デバッグモードで最初に実行する必要があります。 [!DNL log4j.xml]で、`debug`をtrueに設定します。

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Tomcat [!DNL bin]ディレクトリから、サーバーを開始します。

   Linuxの場合：

   ```
   catalina.sh start
   ```

   Windowsの場合：

   ```
   catalina.bat start
   ```
