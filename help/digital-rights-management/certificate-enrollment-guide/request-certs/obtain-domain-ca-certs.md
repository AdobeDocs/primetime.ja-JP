---
title: ドメイン CA 証明書の取得
description: ドメイン CA 証明書の取得
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# ドメイン CA 証明書の取得{#obtain-domain-ca-certificates}

License Server、Packager または Transport 証明書とは異なり、Domain CA 証明書はAdobeによって発行されません。 この証明書は、証明機関から取得することも、この目的で使用する自己署名証明書を生成することもできます。

ドメイン CA 証明書は、1024 ビットキーを使用し、CA 証明書に必要な標準属性を含む必要があります。

* CA フラグが true に設定された Basic Constraints 拡張機能
* 証明書の署名を指定する鍵用途拡張が許可されています

例えば、OpenSSL を使用すると、自己署名 CA 証明書を次のように生成できます。

1. という名前のファイルを作成します。 [!DNL ca-extensions.txt] 次を含む：

   ```
   keyUsage=critical,keyCertSign  
   basicConstraints=critical,CA:TRUE  
   subjectKeyIdentifier=hash 
   ```

1. キーを生成：

   ```
   openssl genrsa -des3 -out domain-ca.key 1024 
   ```

1. CSR を生成：

   ```
   openssl req -new -key domain-ca.key -out domain-ca.csr 
   ```

1. 証明書を生成：

   ```
   openssl x509 -req -days 365 -in domain-ca.csr -signkey domain-ca.key \ 
     -out domain-ca.cer -extfile ca-extensions.txt 
   ```

1. パスワードを生成：

   ```
   openssl rand -base64 8 
   ```

1. PFX を生成：

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```
