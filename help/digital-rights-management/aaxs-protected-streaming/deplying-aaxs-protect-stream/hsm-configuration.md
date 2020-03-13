---
seo-title: HSMの設定
title: HSMの設定
uuid: da4d7118-65a8-460d-a796-b7bf5c28b208
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# HSMの設定 {#hsm-configuration}

HSMを使用してサーバー秘密鍵証明書を保存する場合は、秘密鍵と証明書をHSMに読み込んで、設定ファイルを作成する必要が [!DNL pkcs11.cfg] あります。 このファイルは、 *LicenseServer.ConfigRootディレクトリ内に存在する必要があります* 。 PKCS11設定ファ [!DNL Adobe Access Server for Protected Streaming/configs] イルの例については、Adobe Access DVDのディレクトリを参照してください。 の形式について詳しくは、Sun PKCS11 [!DNL pkcs11.cfg]プロバイダのドキュメントを参照してください。

HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認するには、ファイルが存在するディレクトリ（Java JREおよびJDKと共にインストールされている）から次のコマンドを [!DNL pkcs11.cfg][!DNL keytool] 使用します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに自分の秘密鍵証明書が表示される場合、HSMが正しく設定され、ライセンスサーバーがその秘密鍵証明書にアクセスできるようになります。

> [!NOTE]
> Adobe Access Server for Protected Streamingは、現在、64ビットWindows OS上のHSMをサポートしていません。

