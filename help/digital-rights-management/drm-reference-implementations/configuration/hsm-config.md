---
description: HSMをサポートするSun PKCS#11プロバイダーを使用して、参照の実装を設定できます。 HSMの使用は必須ではありませんが、使用することをお勧めします。
seo-description: HSMをサポートするSun PKCS#11プロバイダーを使用して、参照の実装を設定できます。 HSMの使用は必須ではありませんが、使用することをお勧めします。
seo-title: HSMの設定
title: HSMの設定
uuid: 2741ac40-aa42-4aa7-9864-037f3ed3dee2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# HSM設定{#hsm-configuration}

HSMをサポートするSun PKCS#11プロバイダーを使用して、参照の実装を設定できます。 HSMの使用は必須ではありませんが、使用することをお勧めします。

HSMで秘密鍵証明書を使用するには、Sun PKCS#11プロバイダーの設定ファイルを作成する必要があります。 詳しくは、[Java PCKS#11リファレンスガイド](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html)を参照してください。

HSMおよびSun PKCS#11の設定ファイルが設定されていることを確認するには、Java JDKと共にインストールされたkeytoolを使用して次のコマンドを入力します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストで秘密鍵証明書を表示できる場合は、HSMを正しく設定している必要があります。

>[!NOTE]
>
>Java 1.7以降、64ビットSun Java for Windowsでは、Adobe PrimetimeDRMがHSMデバイスと通信するために必要なPKCS#11インターフェイスをサポートしなくなりました。 HSMを使用する予定がある場合は、32ビット版のJavaを使用するか、完全なPKCS#11インターフェイスをサポートするJDKを使用してください。

