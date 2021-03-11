---
title: ファイルの変換
description: ファイルの変換
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# ファイルを変換{#convert-files}

OpenSSLや秘密鍵などのユーティリティを使用して、リクエスタは、コマンドウィンドウから次のコマンドを入力して、PKCS#12(pfx)およびPEM/DERファイルを生成します。

1. PKCS#7ファイルを一時PEMファイルに変換します。

   OpenSSLを使用するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl pkcs7 -in mycompany-license.p7b -inform DER -out mycompany-license-temp.pem \ 
   -outform PEM -print_certs 
   ```

   >[!NOTE]
   >
   >この一時PEMには、証明書と中間CA用の証明書が含まれます。 PFXファイルを生成するには、次の証明書を使用します。

1. 一時PEMファイルをPFXファイルに変換します。

   OpenSSLを使用するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl pkcs12 -export -inkey mycompany-license.key -in mycompany-license-temp.pem \ 
   -out mycompany-license.pfx -passin pass:private_key_password -passout pass:pfx_password 
   ```

1. 一時PEMファイルを最終PEMファイルに変換します。

   OpenSSLを使用するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl x509 -in mycompany-license-temp.pem -inform PEM -out mycompany-license.pem -outform PEM 
   ```

   >[!NOTE]
   >
   >Adobeでは、秘密鍵(private_key_password)とPFX(pfx_password)に異なるパスワードを使用することをお勧めします。

   この最後のPEMファイルには、自分の証明書のみが含まれます。

1. PEMファイルをDERファイルに変換します。

   OpenSSLを使用するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl x509 -in mycompany-license.pem -inform PEM -out mycompany-license.der -outform DER 
   ```

   >[!NOTE]
   >
   >DERファイルは、HTTP Dynamic Streamingパッケージャーに対してのみ必要です。

