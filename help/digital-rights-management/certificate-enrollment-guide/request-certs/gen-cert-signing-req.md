---
title: 証明書署名要求の生成（要求者）
description: 証明書署名要求の生成（要求者）
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# 証明書署名要求の生成（要求者） {#generate-a-certificate-signing-request-requester}

1. キーペアを生成します。 OpenSSL などのユーティリティを使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobeでは、証明書の種類（lic、pkgr、trans、trial、または eval）をキー名に含めることをお勧めします。 この命名規則を使用すると、ライセンスサーバに配置する際に簡単になります。 この例では、「mycompany-license.key」を使用しています。 評価版および体験版の場合は、「mycompany-eval.key」と「mycompany-trial.key」を使用します。

1. 秘密鍵を保護するためのパスワードを入力します。

   パスワードには少なくとも 12 文字を含める必要があります。 文字には、大文字と小文字の ASCII 文字と数字を混在させる必要があります。 OpenSSL を使用して強力なパスワードを生成するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl rand -base64 8
   ```

1. 証明書署名要求 (CSR) を生成します。

   OpenSSL を使用して CSR を生成するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. 秘密鍵のパスワードを入力するよう求められます。
1. 秘密鍵とパスワードのバックアップコピーを作成します。

   秘密鍵が失われた場合、または秘密鍵が漏洩した場合は、Adobe証明書管理者に連絡して、証明書を失効させ、新しい証明書を要求してください。

   >[!NOTE]
   >
   >Adobeでは、秘密鍵とパスワードを保護するために HSM を使用することをお勧めします。
