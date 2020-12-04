---
seo-title: Javaシステムのプロパティ
title: Javaシステムのプロパティ
uuid: ad1f3d9b-7d95-4e19-a0f8-fd7d4dd4dc32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Javaシステムのプロパティ{#java-system-properties}

次の2つのJava Systemプロパティをオプションで設定して、ライセンスサーバーの設定ファイルとログファイルの場所を変更することができます。

* *LicenseServer.ConfigRoot*  — ライセンスサーバーのすべての設定ファイルが格納されているディレクトリ。これらのファイルの内容について詳しくは、「[ライセンスサーバー構成ファイル](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)」を参照してください。 設定されていない場合のデフォルト値は&#x200B;*CATALINA_BASE/licenseserver*&#x200B;です。
* *LicenseServer.LogRoot*  - 「logs」フォルダーのディレクトリ。ここで、ライセンスサーバーのアプリケーションログが書き込まれます。設定しない場合、デフォルトは&#x200B;*LicenseServer.ConfigRoot*&#x200B;です。

[!DNL catalina.bat]または[!DNL catalina.sh]を使用してTomcatを開始する場合は、`JAVA_OPTS`環境変数を使用して、これらのシステムプロパティを簡単に設定できます。 ここで設定したJavaオプションは、Tomcatの起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

