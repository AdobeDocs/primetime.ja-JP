---
seo-title: HSMの設定
title: HSMの設定
uuid: 1cc5be99-c24c-4c1e-9348-fb69f96d8ca5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# HSMの設定 {#hsm-configuration}

HSMの使用は必須ではありませんが、お勧めします。 参照実装は、Sun PKCS11プロバイダーをHSMサポートに使用するように設定できます。 HSMで秘密鍵証明書を使用するには、Sun PKCS11プロバイダの設定ファイルを作成する必要があります。 詳しくは、Sunのドキュメントを参照してください。 HSMおよびSun PKCS11設定ファイルが正しく設定されていることを確認するには、次のコマンドを使用します（keytoolはJava JDKと共にインストールされます）。

```
    keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
        -providerArg pkcs11.cfg -list
```

自分の秘密鍵証明書がリストに表示される場合、HSMは正しく設定されます。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Java 1.7以降、64ビットSun Java for Windowsは、HSMデバイスと通信するためにAdobe Access DRMで必要なPKCS11インターフェイスをサポートしません。 HSMを使用する場合は、32ビットバージョンのJavaを使用するか、完全なPKCS11インターフェイスをサポートするJDKを使用してください。

