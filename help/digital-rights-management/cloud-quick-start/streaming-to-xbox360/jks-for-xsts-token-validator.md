---
seo-title: XSTSバリデーター用のJKSの作成
title: XSTSバリデーター用のJKSの作成
uuid: e02b517d-0b72-4e95-92b2-09b8f785cce6
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 0%

---


# XSTSバリデーター用のJKSの作成{#create-jks-for-an-xsts-validator}

1. パートナー[!DNL .pfx]ファイルにあるプライベート証明書のエイリアス名を調べます。

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. [!DNL .pfx]を[!DNL .jks]に変換します。

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   （`<alias>`は、手順1で見つけたプライベート証明書のエイリアス名です）。
1. [!DNL x_secure_token_service.part.xboxlive.com.cer]を読み込みます。

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. [!DNL xsts.jks]をTomcatのホームディレクトリに置き、Tomcatの`-Dxsts-keystore-password=****`を定義します。

[!DNL xsts_partner_cert.pfx]と[!DNL xsts.jks]が異なるパスワードを使用している場合は、`jks`の`xsts`パスワードを更新して同じパスワードにします。

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
