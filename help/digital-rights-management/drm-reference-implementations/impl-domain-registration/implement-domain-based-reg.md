---
seo-title: IDベースのドメイン登録の実装
title: IDベースのドメイン登録の実装
uuid: 4a71b2e0-d1a2-4d63-9cbd-980a292774ab
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# IDベースのドメイン登録の実装{#implement-identity-based-domain-registration}

1. 必須ドメイン登録を含むDRMポリシーを作成します。
1. ドメインサーバーのURLに対するサーバーのホストとポートを指定します。

   ファイル内 [!DNL .properties] で、次を設定します。

   ```
   policy.domain.url=https://[server:port] 
   ```

1. ユーザー名とパスワードを使用した認証を必須にします。

   ファイル内 [!DNL .properties] で、次を設定します。

   ```
   policy.domain.anonymous=false 
   ```
