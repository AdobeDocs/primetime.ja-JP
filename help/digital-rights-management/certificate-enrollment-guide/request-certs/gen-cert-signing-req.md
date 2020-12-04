---
seo-title: 証明書署名要求の生成（要求者）
title: 証明書署名要求の生成（要求者）
uuid: 04abd5d2-77ac-4f89-8bea-31d389159aee
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# 証明書署名要求の生成（要求者） {#generate-a-certificate-signing-request-requester}

1. キーペアを生成します。 OpenSSLなどのユーティリティを使用するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobeでは、証明書の種類(lic、pkgr、trans、trial、eval)をキー名に含めることをお勧めします。 この命名規則に従うと、ライセンスサーバに配置しやすくなります。 この例では「mycompany-license.key」を使用しています。 評価版と体験版では、「mycompany-eval.key」と「mycompany-trial.key」を使用します。

1. 秘密鍵を保護するためのパスワードを入力します。

   パスワードは12文字以上にする必要があります。 これらの文字には、ASCII文字の大文字と小文字を組み合わせたものと、数字を含める必要があります。 OpenSSLを使用して堅牢なパスワードを生成するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl rand -base64 8
   ```

1. 証明書署名要求(CSR)を生成します。

   OpenSSLを使用してCSRを生成するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. 秘密鍵のパスワードを入力するよう求められます。
1. 秘密鍵とパスワードのバックアップコピーを作成します。

   秘密鍵を失った場合、または秘密鍵が侵害された場合は、Adobe証明書管理者に問い合わせて、証明書を無効にし、新しい証明書を要求してください。

   >[!NOTE]
   >
   >Adobeでは、秘密鍵とパスワードを保護するために、HSMを使用することをお勧めします。

