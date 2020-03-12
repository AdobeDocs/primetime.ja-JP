---
description: HSMをサポートするSun PKCS#11プロバイダーを使用して、参照実装を設定できます。 HSMの使用は必須ではありませんが、推奨されます。
seo-description: HSMをサポートするSun PKCS#11プロバイダーを使用して、参照実装を設定できます。 HSMの使用は必須ではありませんが、推奨されます。
seo-title: HSMの設定
title: HSMの設定
uuid: 2741ac40-aa42-4aa7-9864-037f3ed3dee2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# HSMの設定{#hsm-configuration}

HSMをサポートするSun PKCS#11プロバイダーを使用して、参照実装を設定できます。 HSMの使用は必須ではありませんが、推奨されます。

HSMで秘密鍵証明書を使用するには、Sun PKCS#11プロバイダの設定ファイルを作成する必要があります。 詳しくは、 [Java PCKS#11リファレンスガイドを参照してください](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html)。

HSMおよびSun PKCS#11設定ファイルが設定されていることを確認するには、Java JDKと共にインストールされたkeytoolを使用して次のコマンドを入力します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

秘密鍵証明書をリストに表示できる場合は、HSMを正しく設定しています。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Java 1.7以降、64ビットSun Java for Windowsでは、Adobe Primetime DRMがHSMデバイスと通信するために必要なPKCS#11インターフェイスをサポートしなくなりました。 HSMを使用する場合は、32ビットバージョンのJavaを使用するか、完全なPKCS#11インターフェイスをサポートするJDKを使用してください。

