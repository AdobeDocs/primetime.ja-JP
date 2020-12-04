---
description: サーバーの秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。
seo-description: サーバーの秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。
seo-title: HSMの設定
title: HSMの設定
uuid: 3610840b-082e-4a73-8aa5-5065f9232e0b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# HSM設定{#hsm-configuration}

サーバーの秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。

設定ファイルは、*LicenseServer.ConfigRoot*&#x200B;ディレクトリにある必要があります。

PKCS11設定ファイルの例については、Adobe PrimetimeDRM DVDの[!DNL Adobe Primetime DRM Server for Protected Streaming/configs]ディレクトリを参照してください。

[!DNL pkcs11.cfg]ファイルの形式に関するSun PKCS11プロバイダーのドキュメントを参照してください。

[!DNL pkcs11.cfg]ファイルが存在するディレクトリ（[!DNL keytool]はJava JREおよびJDKと共にインストールされています）で次のコマンドを使用して、HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認できます。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストで秘密鍵証明書を表示できる場合、HSMは正しく設定され、ライセンスサーバーはこれで秘密鍵証明書にアクセスできるようになります。
