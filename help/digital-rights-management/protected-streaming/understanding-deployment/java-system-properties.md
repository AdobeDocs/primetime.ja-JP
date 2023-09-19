---
description: ライセンスサーバー上で構成して、構成ファイルとログファイルの場所を制御する Java システムのプロパティがいくつかあります。
title: Java システムプロパティ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Java システムプロパティ{#java-system-properties}

ライセンスサーバー上で構成して、構成ファイルとログファイルの場所を制御する Java システムのプロパティがいくつかあります。

オプションで、次の Java System プロパティを設定できます。

* *`LicenseServer.ConfigRoot`*  — ライセンスサーバの構成ファイルを含むディレクトリの名前。

  詳しくは、 *ライセンスサーバの設定ファイル* を参照してください。 設定されていない場合、デフォルト値は `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot*  — 名前： [!DNL logs] ライセンスサーバーのアプリケーションログが保存されるディレクトリ。 このディレクトリの名前を変更していない場合、このディレクトリの名前は *LicenseServer.ConfigRoot* デフォルトでは。

を使用する場合、 [!DNL catalina.bat] または [!DNL catalina.sh] Tomcat を起動するファイルを使用する場合は、 `JAVA_OPTS` 環境変数。 設定した Java オプションは、Tomcat の起動時に自動的に適用されます。

例えば、 `JAVA_OPTS` 環境変数の内容を次に示します。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
