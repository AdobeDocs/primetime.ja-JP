---
title: 保護されたストリーミング用のサーバーのセットアップとデプロイ
description: 保護されたストリーミング用のサーバーのセットアップとデプロイ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 保護されたストリーミング用のサーバーのセットアップとデプロイ {#set-up-and-deploy-the-server-for-protected-streaming}

1. Primetime DRM DVD で設定フォルダーを設定します。

   `\Adobe Access Server for Protected Streaming\configs\`
1. サンプルをコピー `configs` 次のフォルダーに移動： `<Tomcat_installation_dir>` コピーしたフォルダーの名前をに変更します。 `licenseserver`.

   これで、configs フォルダーのパスが `<Tomcat_install_dir>\licenseserver\`.
1. 実行 `Scrambler.bat` Primetime DRM でトランスポートおよびライセンスサーバーの PFX ファイル用の暗号化されたパスワードを取得するには `<DVD>` `\Adobe Access Server for Protected Streaming\` ディレクトリ：

   * `Scrambler.bat <Adobe-provided transport credential password>`
   * `Scrambler.bat <Adobe-provided license server credential password>`

1. PFX ファイルを `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\<tenant-name>\` ディレクトリ。
1. で対応するテナント設定を編集します。 `<TomcatInstallDir>\licenseserver\flashaccessserver\tenants\sampletenant\flashaccess-tenant.xml`（以下の設定）

   ```
   Configuration|Tenant|Credentials|TransportCredential|File|path=<filename-transport-credential-PFX> 
   Configuration|Tenant|Credentials|TransportCredential|File|password=<scrambled-transportcredential-password> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|path=<fielname-license-servercredential-PFX> 
   Configuration|Tenant|Credentials|LicenseServerCredential|File|password=<scrambled-license-servercredential-password>
   ```

1. を実行します。 `Validator.bat` 設定を検証するユーティリティは、次のように有効です。

   ```
   Validator.bat -g -r <absolute-path-to TomcatInstallDir\licenseserver>
   ```

1. をコピーします。 `flashaccessserver.war` ファイルを CD から `<TomcatInstallDir>\webapps\` ディレクトリ。
1. Tomcat が実行中の場合は、「 `<CTRL-C>` （コマンドウィンドウから起動した場合）。 また、Tomcat が Windows サービスとしてインストールされている場合は、Windows Services アプリケーションからサーバーを停止することもできます。
1. Tomcat を起動するには、次のコマンドを入力します。

   ```
   <TomcatInstallDir>\bin\catalina run
   ```

1. 設定を確認するには、ブラウザーに次の URL を入力します。

   ```
    https://<LicenseServer>:8080/flashaccessserver/flashaccess/license/v2
   ```
