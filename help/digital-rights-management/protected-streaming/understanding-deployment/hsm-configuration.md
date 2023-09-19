---
description: サーバーの資格情報を保存する HSM を選択する場合は、秘密鍵と証明書を HSM に読み込み、pkcs11.cfg 設定ファイルを作成する必要があります。
title: HSM 設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# HSM 設定{#hsm-configuration}

サーバーの資格情報を保存する HSM を選択する場合は、秘密鍵と証明書を HSM に読み込み、pkcs11.cfg 設定ファイルを作成する必要があります。

設定ファイルは、 *LicenseServer.ConfigRoot* ディレクトリ。

詳しくは、 [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] Adobe Primetime DRM DVD 上のディレクトリ（サンプルの PKCS11 構成ファイル用）。

の形式に関する Sun PKCS11 プロバイダのドキュメントを参照してください。 [!DNL pkcs11.cfg] ファイル。

次のコマンドは、 [!DNL pkcs11.cfg] ファイルが見つかりました ( [!DNL keytool] は、HSM および Sun PKCS11 設定ファイルが正しく設定されていることを確認するために、Java JRE および JDK と共にインストールされます。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに認証情報が表示される場合は、HSM が正しく設定され、ライセンスサーバーがその認証情報にアクセスできるようになります。
