---
seo-title: ドメインCA証明書の取得
title: ドメインCA証明書の取得
uuid: 41bbe02b-363a-47f4-9cc0-350730b6c787
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# ドメインCA証明書の取得{#obtain-domain-ca-certificates}

License Server、Packager、またはTransport証明書とは異なり、ドメインCA証明書はアドビから発行されません。 この証明書は、認証局から取得するか、この目的で使用する自己署名証明書を生成することができます。

ドメインCA証明書は、1024ビットキーを使用し、CA証明書に必要な標準属性を含む必要があります。

* CAフラグがtrueに設定された基本制約拡張
* 証明書の署名を指定する鍵用途拡張が許可されます

例えば、OpenSSLを使用して、自己署名CA証明書を次のように生成できます。

1. 次を含むというファイルを [!DNL ca-extensions.txt] 作成します。

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

1. PFXの生成：

   ```
   openssl pkcs12 -export -inkey domain-ca.key \ 
   -in domain-ca.cer -out domain-ca.pfx
   ```

