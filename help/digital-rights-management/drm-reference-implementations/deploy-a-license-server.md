---
title: ライセンスサーバーのデプロイ
description: ライセンスサーバーのデプロイ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ライセンスサーバーのデプロイ{#deploy-the-license-server}

1. 参照実装の war ファイルを `webapps` Tomcat サーバー上のディレクトリ。

   参照実装ライセンスサーバをそのまま使用するには、ライセンスサーバの WAR ファイル ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\\flashaccess.war`) を `webapps` Tomcat サーバー上のディレクトリ。

   参照実装ライセンスサーバーをカスタマイズする場合は、作成したサーバー war ファイルをコピーします。 `DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl-build\wars` から `webapps` ディレクトリ。

   >[!NOTE]
   >
   >ライセンスサーバの WAR ファイルを以前に展開した場合は、 [!DNL webapps] Tomcat サーバー上のディレクトリ：
   >
   >* [!DNL webapps/flashaccess]
   >* [!DNL webapps/edcws]

   >[!NOTE]
   >
   >デプロイしない [!DNL edsws.war] ただし、FlashメディアRights Management(FMRMS)v1.5 コンテンツとの下位互換性が必要な場合を除きます。 （これは非常にまれな要件です。）
   >
   >Tomcat による WAR ファイルの展開を防ぐ場合は、 `server.xml` （内） `conf` ディレクトリとセット `unpackWARs` から `false`.

1. のコンテンツ全体をコピーする `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources\` のディレクトリに [!DNL tomcat] ディレクトリ。

   The [!DNL resources] 次のディレクトリが含まれます。

   * [!DNL flashaccesstools.properties]  — ライセンスサーバーのプロパティファイル。
   * [!DNL log4j.xml]  — ライセンスサーバのログ設定
   * [!DNL *.pol] - DRM ポリシーファイルのサンプル。

   また、この場所にAdobe証明書ファイルをコピーすることもできます。

1. でライセンスサーバの設定を変更する [!DNL flashaccesstools.properties] を追加して、サーバー設定を反映させます。

   少なくとも、次のプロパティに値を設定します。

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

1. を編集します。 `catalina.properties` Tomcat 内のファイル `conf` ディレクトリ。 [!DNL resources] ディレクトリ（またはプロパティファイルおよびその他のリソースファイルを保存した代替の場所）を `shared.loader` プロパティ。

   例えば、 `flashaccess-refimpl.properties` [!DNL にあります [Tomcat ホーム]\resources\]:

   ```
   shared.loader=..\resources
   ```

   この場所 `flashaccess-refimpl.properties` クラスパスの
1. 他のリソースファイル ( [!DNL log4j.xml]、ポリシーファイル、証明書 ) は、 [!DNL resources] ディレクトリ、またはクラスパス上に存在しない場合は、 [!DNL flashaccess-refimpl.properties].

   最初にを実行するとよいでしょう。 `log4j` デバッグモードで。 In [!DNL log4j.xml]，設定 `debug` を true に設定します。

   ```
   <log4j:configuration xmlns:log4j="https://jakarta.apache.org/log4j/"<b>debug="true"</b>>
   ...
   ```

1. Tomcat から [!DNL bin] ディレクトリに移動し、サーバーを起動します。

   Linux の場合：

   ```
   catalina.sh start
   ```

   Windows の場合：

   ```
   catalina.bat start
   ```
