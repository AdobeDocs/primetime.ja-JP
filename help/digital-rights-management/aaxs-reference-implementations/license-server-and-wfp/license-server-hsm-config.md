---
seo-title: HSMの設定
title: HSMの設定
uuid: 1cc5be99-c24c-4c1e-9348-fb69f96d8ca5
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# HSMの設定 {#hsm-configuration}

HSMの使用は必須ではありませんが、推奨されます。 参照の実装は、Sun PKCS11プロバイダー（HSMサポート用）を使用するように設定できます。 HSMで秘密鍵証明書を使用するには、Sun PKCS11プロバイダーの設定ファイルを作成する必要があります。 詳しくは、Sunのマニュアルを参照してください。 HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認するには、次のコマンドを使用します（keytoolはJava JDKと共にインストールされます）。

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

秘密鍵証明書がリストに表示される場合は、HSMが正しく設定されています。

>[!NOTE]
>
>Java 1.7以降、64ビットのSun Java for Windowsでは、HSMデバイスと通信するためにAdobeアクセスDRMに必要なPKCS11インターフェイスをサポートしません。 HSMを使用する予定がある場合は、32ビット版のJavaを使用するか、完全なPKCS11インターフェイスをサポートするJDKを使用してください。

