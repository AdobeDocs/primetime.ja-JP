---
title: HSM 設定
description: HSM 設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# HSM 設定 {#hsm-configuration}

HSM を使用してサーバーの資格情報を保存する場合は、秘密鍵と証明書を HSM に読み込み、 [!DNL pkcs11.cfg] 設定ファイル。 このファイルは、 *LicenseServer.ConfigRoot* ディレクトリ。 詳しくは、 [!DNL Adobe Access Server for Protected Streaming/configs] AdobeAccess DVD のディレクトリ（PKCS11 構成ファイルの例）。 の形式について詳しくは、 [!DNL pkcs11.cfg]（ Sun PKCS11 プロバイダのドキュメントを参照）。

HSM および Sun PKCS11 の設定ファイルが正しく設定されていることを確認するには、次のコマンドを、 [!DNL pkcs11.cfg] ファイルが見つかりました ( [!DNL keytool] は、Java JRE および JDK と共にインストールされます )。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに自分の資格情報が表示された場合は、HSM が正しく設定され、ライセンスサーバーがその資格情報にアクセスできるようになります。

>[!NOTE]
>
>Adobeアクセスサーバー（保護ストリーミング用）は、現在、64 ビット Windows OS での HSM をサポートしていません。
