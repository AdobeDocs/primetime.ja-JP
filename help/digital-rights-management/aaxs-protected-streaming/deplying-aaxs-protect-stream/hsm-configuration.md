---
title: HSMの設定
description: HSMの設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# HSM設定{#hsm-configuration}

HSMを使用してサーバーの秘密鍵証明書を保存する場合は、秘密鍵と証明書をHSMに読み込んで、[!DNL pkcs11.cfg]設定ファイルを作成する必要があります。 このファイルは、*LicenseServer.ConfigRoot*&#x200B;ディレクトリに存在する必要があります。 AdobeアクセスDVDの[!DNL Adobe Access Server for Protected Streaming/configs]ディレクトリを参照して、PKCS11設定ファイルの例を確認してください。 [!DNL pkcs11.cfg]の形式について詳しくは、Sun PKCS11プロバイダーのドキュメントを参照してください。

HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認するには、[!DNL pkcs11.cfg]ファイルが存在するディレクトリ（[!DNL keytool]はJava JREおよびJDKと共にインストールされています）から次のコマンドを使用します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに秘密鍵証明書が表示されている場合、HSMが正しく設定され、ライセンスサーバーがその秘密鍵証明書にアクセスできるようになります。

>[!NOTE]
>
>保護されたストリーミング用のAdobeアクセスサーバーは、現在、64ビットWindows OS上のHSMをサポートしていません。
