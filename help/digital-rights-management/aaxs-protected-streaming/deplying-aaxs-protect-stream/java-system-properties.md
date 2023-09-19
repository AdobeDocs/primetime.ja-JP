---
title: Java システムプロパティ
description: Java システムプロパティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Java システムプロパティ {#java-system-properties}

次の 2 つの Java System プロパティを、ライセンスサーバーの構成ファイルとログファイルの場所を変更するように設定することもできます。

* *LicenseServer.ConfigRoot*  — ライセンスサーバーのすべての構成ファイルを含むディレクトリ。 これらのファイルの内容について詳しくは、[ライセンスサーバの設定ファイル](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. 設定しない場合、デフォルトはです。 *CATALINA_BASE/licenseserver*.
* *LicenseServer.LogRoot*  — ライセンスサーバーアプリケーションのログが書き込まれる「logs」フォルダのディレクトリ。 設定しない場合、デフォルトはです。 *LicenseServer.ConfigRoot*.

を使用している場合、 [!DNL catalina.bat] または [!DNL catalina.sh] Tomcat を起動するには、以下のシステムプロパティを `JAVA_OPTS` 環境変数。 ここで設定した Java オプションは、Tomcat の起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
