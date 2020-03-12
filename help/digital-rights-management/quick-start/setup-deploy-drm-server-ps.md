---
seo-title: 保護されたストリーミング用のサーバーの設定と展開
title: 保護されたストリーミング用のサーバーの設定と展開
uuid: 300a1b63-0bf0-48a8-977d-212563025c19
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# 保護されたストリーミング用のサーバーの設定と展開 {#set-up-and-deploy-the-server-for-protected-streaming}

1. Primetime DRM DVDの設定フォルダーを設定します。

   `\Adobe Access Server for Protected Streaming\configs\`
1. サンプルフォルダ `configs` ーをにコピーし、 `<Tomcat_installation_dir>` コピーしたフォルダーの名前をに変更しま `licenseserver`す。

   configsフォルダーのパスは、次のようになりま `<Tomcat_install_dir>\licenseserver\`す。
1. を実行し `Scrambler.bat` て、Primetime DRMディレクトリ内のトランスポートおよびライセンスサーバーのPFXファイルの暗号化されたパスワードを取得 `<DVD>` しま `\Adobe Access Server for Protected Streaming\` す。

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. PFXファイルをディレクトリにコピー `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` します。
1. 次の設定で、対応するテナ `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`ント設定を編集します。

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. ユーティリテ `Validator.bat` ィを実行し、構成が有効であることを確認します。

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. CDからデ `flashaccessserver.war` ィレクトリにファイルをコピー `<TomcatInstallDir>\webapps\` します。
1. Tomcatが実行中の場合は、コマンドウィンドウ内を押して(コマンドウィ `<CTRL-C>` ンドウから起動した場合)、実行中のTomcatインスタンスを停止します。 また、TomcatがWindowsサービスとしてインストールされている場合は、Windowsサービスアプリケーションからサーバーを停止することもできます。
1. Tomcatを起動するには、次のコマンドを入力します。

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. 設定を確認するには、ブラウザーに次のURLを入力します。

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
