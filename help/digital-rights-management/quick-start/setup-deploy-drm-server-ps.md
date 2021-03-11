---
title: 保護されたストリーミング用のサーバーの設定と展開
description: 保護されたストリーミング用のサーバーの設定と展開
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# 保護されたストリーミング用にサーバーをセットアップし、展開する{#set-up-and-deploy-the-server-for-protected-streaming}

1. Primetime DRM DVDの設定フォルダーを設定します。

   `\Adobe Access Server for Protected Streaming\configs\`
1. サンプル`configs`フォルダーを`<Tomcat_installation_dir>`にコピーし、コピーしたフォルダーの名前を`licenseserver`に変更します。

   configsフォルダーのパスは、次に`<Tomcat_install_dir>\licenseserver\`になります。
1. `Scrambler.bat`を実行し、Primetime DRM `<DVD>` `\Adobe Access Server for Protected Streaming\`ディレクトリ内のトランスポートおよびライセンスサーバーのPFXファイル用の暗号化されたパスワードを取得します。

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. PFXファイルを`<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\`ディレクトリにコピーします。
1. `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`の対応するテナント構成を次の設定で編集します。

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. `Validator.bat`ユーティリティを実行して、構成が有効であることを確認します。

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. `flashaccessserver.war`ファイルをCDから`<TomcatInstallDir>\webapps\`ディレクトリにコピーします。
1. Tomcatが実行中の場合は、コマンドウィンドウで`<CTRL-C>`を押して、実行中のTomcatインスタンスを停止します（コマンドウィンドウから起動した場合）。 また、TomcatがWindowsサービスとしてインストールされている場合は、Windowsサービスアプリケーションからサーバーを停止することもできます。
1. Tomcatを開始するには、次のコマンドを入力します。

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. 設定を確認するには、ブラウザーに次のURLを入力します。

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
