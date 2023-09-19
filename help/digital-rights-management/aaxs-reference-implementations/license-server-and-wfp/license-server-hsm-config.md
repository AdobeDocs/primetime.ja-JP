---
title: HSM 設定
description: HSM 設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# HSM 設定 {#hsm-configuration}

HSM の使用は必須ではありませんが、推奨します。 参照実装は、Sun PKCS11 プロバイダを HSM サポートに使用するように設定できます。 HSM で秘密鍵証明書を使用するには、Sun PKCS11 プロバイダの設定ファイルを作成する必要があります。 詳しくは、 Sun のマニュアルを参照してください。 HSM および Sun PKCS11 の設定ファイルが正しく設定されていることを確認するには、次のコマンドを使用します（keytool は Java JDK と共にインストールされます）。

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

リストに自分の資格情報が表示される場合は、HSM が正しく設定されています。

>[!NOTE]
>
>Java 1.7 以降、64 ビット Sun Java for Windows は、HSM デバイスとの通信にAdobeアクセス DRM が必要とする PKCS11 インターフェイスをサポートしていません。 HSM を使用する場合は、32 ビット版の Java を使用するか、完全な PKCS11 インターフェイスをサポートする JDK を使用してください。
