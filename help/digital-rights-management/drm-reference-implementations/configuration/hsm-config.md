---
description: HSM をサポートする Sun PKCS#11 プロバイダを使用して、参照実装を設定できます。 HSM は必須ではありませんが、使用することをお勧めします。
title: HSM 設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# HSM 設定{#hsm-configuration}

HSM をサポートする Sun PKCS#11 プロバイダを使用して、参照実装を設定できます。 HSM は必須ではありませんが、使用することをお勧めします。

HSM で秘密鍵証明書を使用するには、Sun PKCS#11 プロバイダの設定ファイルを作成する必要があります。 詳しくは、 [Java PCKS#11 リファレンスガイド](https://docs.oracle.com/javase/1.5.0/docs/guide/security/p11guide.html).

HSM および Sun PKCS#11 の設定ファイルが設定されていることを確認するには、Java JDK と共にインストールされた keytool を使用して、次のコマンドを入力します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに資格情報が表示される場合は、HSM を正しく設定しています。

>[!NOTE]
>
>Java 1.7 以降、64 ビット Sun Java for Windows は、Adobe Primetime DRM が HSM デバイスと通信するために必要な PKCS#11 インターフェイスをサポートしなくなりました。 HSM を使用する場合は、必ず 32 ビットバージョンの Java を使用するか、完全な PKCS#11 インターフェイスをサポートする JDK を使用してください。
