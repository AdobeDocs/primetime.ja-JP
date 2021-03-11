---
description: サーバーの秘密鍵証明書を保存するHSMを選択する場合は、秘密鍵と証明書をHSMに読み込み、pkcs11.cfg設定ファイルを作成する必要があります。
title: HSMの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
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
