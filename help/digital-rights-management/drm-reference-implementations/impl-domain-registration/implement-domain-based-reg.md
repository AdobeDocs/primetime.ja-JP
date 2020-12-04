---
seo-title: IDベースのドメイン登録の実装
title: IDベースのドメイン登録の実装
uuid: 4a71b2e0-d1a2-4d63-9cbd-980a292774ab
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# IDベースのドメイン登録{#implement-identity-based-domain-registration}の実装

1. 必須のドメイン登録を含むDRMポリシーを作成します。
1. サーバーのホストとドメインサーバーのURLのポートを指定します。

   [!DNL .properties]ファイルに次を設定します。

   ```
   policy.domain.url=https://[server:port] 
   ```

1. ユーザー名とパスワードを必須にして認証します。

   [!DNL .properties]ファイルに次を設定します。

   ```
   policy.domain.anonymous=false 
   ```
