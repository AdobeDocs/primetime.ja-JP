---
title: ドメインCA証明書の取得
description: ドメインCA証明書の取得
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# ドメインCA証明書の取得{#obtain-domain-ca-certificates}

License Server、Packager、またはトランスポート証明書とは異なり、ドメインCA証明書はAdobeによって発行されません。 この証明書は認証局から取得するか、この目的で使用する自己署名証明書を生成することができます。

ドメインCA証明書は、1024ビットキーを使用し、CA証明書に必要な標準属性を含む必要があります。

* CAフラグがtrueに設定された基本制約拡張
* 証明書署名を指定する鍵用途拡張が許可されます

例えば、OpenSSLを使用して、自己署名CA証明書を次のように生成できます。

1. [!DNL ca-extensions.txt]という名前のファイルを作成し、次を含めます。

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. キーの生成：

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. CSRの生成：

   ```
   openssl req -new -key domain-ca.key -out domain-ca.csr 
   ```

1. 証明書の生成：

   ```
   openssl x509 -req -days 365 -in domain-ca.csr -signkey domain-ca.key \ 
     -out domain-ca.cer -extfile ca-extensions.txt 
   ```

1. パスワードの生成：

   ```
   openssl rand -base64 8 
   ```

1. PFXを生成：

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```

