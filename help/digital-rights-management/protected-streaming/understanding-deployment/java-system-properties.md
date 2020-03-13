---
description: 設定ファイルとログファイルの場所を制御するために、ライセンスサーバー上で設定できるJava Systemプロパティがいくつかあります。
seo-description: 設定ファイルとログファイルの場所を制御するために、ライセンスサーバー上で設定できるJava Systemプロパティがいくつかあります。
seo-title: Javaシステムのプロパティ
title: Javaシステムのプロパティ
uuid: d8c72359-bf61-47e0-9cd5-b21225d5fe49
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Javaシステムのプロパティ{#java-system-properties}

設定ファイルとログファイルの場所を制御するために、ライセンスサーバー上で設定できるJava Systemプロパティがいくつかあります。

必要に応じて、次のJava Systemプロパティを設定できます。

* *`LicenseServer.ConfigRoot`* — ライセンスサーバーの設定ファイルを含むディレクトリの名前。

   これらのフ *ァイルの内容について詳しくは* 、「ライセンスサーバー設定ファイル」を参照してください。 設定しなかった場合、デフォルト値はです `CATALINA_BASE/licenseserver`。

* *LicenseServer.LogRoot* — ライセンスサーバー [!DNL logs] のアプリケーションログが格納されているディレクトリの名前。 このディレクトリの名前を変更していない場合、このディレクトリの名前はデフォルトで *LicenseServer.ConfigRootとして設定されます* 。

またはファイルを使 [!DNL catalina.bat] 用し [!DNL catalina.sh] てTomcatを起動する場合は、環境変数を使用してシステムプロパティを設定 `JAVA_OPTS` できます。 設定したJavaオプションは、Tomcatの起動時に自動的に適用されます。

例えば、次のように環境変数 `JAVA_OPTS` を設定できます。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

