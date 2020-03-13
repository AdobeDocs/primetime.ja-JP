---
description: サーバー秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。
seo-description: サーバー秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。
seo-title: HSMの設定
title: HSMの設定
uuid: 3610840b-082e-4a73-8aa5-5065f9232e0b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# HSMの設定{#hsm-configuration}

サーバー秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。

設定ファイルは、 *LicenseServer.ConfigRootディレクトリ内にある必要があります* 。

PKCS11設定ファ [!DNL Adobe Primetime DRM Server for Protected Streaming/configs] イルの例については、Adobe Primetime DRM DVDのディレクトリを参照してください。

ファイルの形式に関するSun PKCS11プロバイダのドキュメントを参照して [!DNL pkcs11.cfg] ください。

ファイルが存在するディレクトリ(Java JREおよび [!DNL pkcs11.cfg][!DNL keytool] JDKと共にインストールされている)から次のコマンドを使用して、HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認できます。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

秘密鍵証明書をリストに表示できる場合は、HSMが正しく設定され、ライセンスサーバーが秘密鍵証明書にアクセスできるようになります。
