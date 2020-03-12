---
seo-title: Javaシステムのプロパティ
title: Javaシステムのプロパティ
uuid: ad1f3d9b-7d95-4e19-a0f8-fd7d4dd4dc32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Javaシステムのプロパティ {#java-system-properties}

次の2つのJava Systemプロパティをオプションで設定して、ライセンスサーバーの設定ファイルとログファイルの場所を変更できます。

* *LicenseServer.ConfigRoot* — ライセンスサーバーのすべての設定ファイルを含むディレクトリ。 これらのファイルの内容について詳しくは、「[License server configuration files](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)」を参照してください。 設定しなかった場合、デフォル *トはCATALINA_BASE/licenseserverです*。
* *LicenseServer.LogRoot* — ライセンスサーバーのアプリケーションログが書き込まれる「logs」フォルダのディレクトリ。 設定しなかった場合、デフォルト *はLicenseServer.ConfigRootです*。

またはを使用してTomcatを起 [!DNL catalina.bat] 動する [!DNL catalina.sh] 場合、これらのシステムプロパティは、環境変数を使用して簡単に設定 `JAVA_OPTS` できます。 ここで設定したJavaオプションは、Tomcatの起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

