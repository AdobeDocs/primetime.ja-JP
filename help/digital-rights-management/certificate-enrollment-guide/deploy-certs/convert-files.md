---
title: ファイルを変換
description: ファイルを変換
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# ファイルを変換{#convert-files}

OpenSSL や秘密鍵などのユーティリティを使用して、リクエスターは、コマンドウィンドウから次のコマンドを入力して、PKCS#12 (pfx) および PEM/DER ファイルを生成します。

1. PKCS#7 ファイルを一時 PEM ファイルに変換します。

   OpenSSL を使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >この一時的な PEM には、証明書と中間 CA 用の証明書が含まれます。 これらの証明書を使用して PFX ファイルを生成します。

1. 一時 PEM ファイルを PFX ファイルに変換します。

   OpenSSL を使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl pkcs12 -export -inkey mycompany-license.key -in mycompany-license-temp.pem \ 
   -out mycompany-license.pfx -passin pass:private_key_password -passout pass:pfx_password 
   ```

1. 一時 PEM ファイルを最終 PEM ファイルに変換します。

   OpenSSL を使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl x509 -in mycompany-license-temp.pem -inform PEM -out mycompany-license.pem -outform PEM 
   ```

   >[!NOTE]
   >
   >Adobeでは、必須ではありませんが、秘密鍵 (private_key_password) と PFX(pfx_password) に異なるパスワードを使用することをお勧めします。

   この最終的な PEM ファイルには、証明書のみが含まれています。

1. PEM ファイルを DER ファイルに変換します。

   OpenSSL を使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >DER ファイルは、HTTP Dynamic Streamingパッケージャにのみ必要です。
