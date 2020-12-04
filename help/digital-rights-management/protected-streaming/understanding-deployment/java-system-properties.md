---
description: 設定ファイルとログファイルの場所を制御するために、ライセンスサーバー上で設定できるJava Systemプロパティがいくつかあります。
seo-description: 設定ファイルとログファイルの場所を制御するために、ライセンスサーバー上で設定できるJava Systemプロパティがいくつかあります。
seo-title: Javaシステムのプロパティ
title: Javaシステムのプロパティ
uuid: d8c72359-bf61-47e0-9cd5-b21225d5fe49
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Javaシステムのプロパティ{#java-system-properties}

設定ファイルとログファイルの場所を制御するために、ライセンスサーバー上で設定できるJava Systemプロパティがいくつかあります。

必要に応じて、次のJava Systemプロパティを設定できます。

* *`LicenseServer.ConfigRoot`*  — ライセンスサーバの構成ファイルを含むディレクトリの名前。

   これらのファイルの内容について詳しくは、*ライセンスサーバー構成ファイル*&#x200B;を参照してください。 設定しなかった場合、デフォルト値は`CATALINA_BASE/licenseserver`です。

* *LicenseServer.LogRoot*  — ライセンスサーバーアプリケーションログが格納されている [!DNL logs] ディレクトリの名前。このディレクトリの名前を変更していない場合、このディレクトリの名前は、デフォルトで&#x200B;*LicenseServer.ConfigRoot*&#x200B;として設定されます。

[!DNL catalina.bat]または[!DNL catalina.sh]ファイルを使用してTomcatを開始する場合は、`JAVA_OPTS`環境変数を使用してSystemプロパティを設定できます。 設定したJavaオプションは、Tomcat開始時に自動的に適用されます。

例えば、`JAVA_OPTS`環境変数は次のように設定できます。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

