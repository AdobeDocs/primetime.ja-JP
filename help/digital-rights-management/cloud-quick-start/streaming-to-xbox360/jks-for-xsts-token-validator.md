---
seo-title: XSTSバリデーター用のJKSの作成
title: XSTSバリデーター用のJKSの作成
uuid: e02b517d-0b72-4e95-92b2-09b8f785cce6
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# XSTSバリデーター用のJKSの作成{#create-jks-for-an-xsts-validator}

1. パートナーファイル内のプライベート証明書のエイリアス名を確認し [!DNL .pfx] ます。

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. に変 [!DNL .pfx] 換しま [!DNL .jks]す。

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (ここ `<alias>` では、手順1で見つけたプライベート証明書のエイリアス名です)。
1. インポート [!DNL x_secure_token_service.part.xboxlive.com.cer]:

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Tomcatのホ [!DNL xsts.jks] ームディレクトリに置き、Tomcat用に定義 `-Dxsts-keystore-password=****` します。

とで異な [!DNL xsts_partner_cert.pfx] るパスワ [!DNL xsts.jks] ードを使用している場合は、でパスワードを `xsts` 更新して同 `jks` じパスワードにします。

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
