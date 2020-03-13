---
seo-title: 証明書署名要求の生成（要求者）
title: 証明書署名要求の生成（要求者）
uuid: 04abd5d2-77ac-4f89-8bea-31d389159aee
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# 証明書署名要求の生成（要求者） {#generate-a-certificate-signing-request-requester}

1. キーペアを生成します。 OpenSSLなどのユーティリティを使用するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >証明書の種類（lic、pkgr、trans、trialまたはeval）をキー名に含めることをお勧めします。 この命名規則により、ライセンスサーバにデプロイする際の作業が簡単になります。 この例では、「mycompany-license.key」を使用しています。 評価版と体験版の場合は、「mycompany-eval.key」と「mycompany-trial.key」を使用します。

1. 秘密鍵を保護するためのパスワードを入力します。

   パスワードは12文字以上にする必要があります。 文字には、大文字と小文字のASCII文字と数字を混在させる必要があります。 OpenSSLを使用して強力なパスワードを生成するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl rand -base64 8
   ```

1. 証明書署名要求(CSR)の生成を参照してください。

   OpenSSLを使用してCSRを生成するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. 秘密鍵のパスワードの入力を求められます。
1. 秘密鍵とパスワードのバックアップコピーを作成します。

   秘密鍵を紛失した場合、または秘密鍵が侵害された場合は、Adobe証明書管理者に問い合わせて、証明書を失効させ、新しい証明書を要求します。

   >[!NOTE]
   >
   >秘密鍵とパスワードを保護するために、HSMを使用することをお勧めします。

