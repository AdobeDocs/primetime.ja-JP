---
title: Javaシステムのプロパティ
description: Javaシステムのプロパティ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Javaシステムのプロパティ{#java-system-properties}

次の2つのJava Systemプロパティをオプションで設定して、ライセンスサーバーの設定ファイルとログファイルの場所を変更することができます。

* *LicenseServer.ConfigRoot*  — ライセンスサーバーのすべての設定ファイルが格納されているディレクトリ。これらのファイルの内容について詳しくは、「[ライセンスサーバー構成ファイル](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)」を参照してください。 設定しなかった場合のデフォルト値は&#x200B;*CATALINA_BASE/licenseserver*&#x200B;です。
* *LicenseServer.LogRoot*  - 「logs」フォルダーのディレクトリ。ここで、ライセンスサーバーのアプリケーションログが書き込まれます。設定しない場合、デフォルトは&#x200B;*LicenseServer.ConfigRoot*&#x200B;です。

[!DNL catalina.bat]または[!DNL catalina.sh]を使用してTomcatを開始する場合は、`JAVA_OPTS`環境変数を使用して、これらのシステムプロパティを簡単に設定できます。 ここで設定したJavaオプションは、Tomcatの起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

