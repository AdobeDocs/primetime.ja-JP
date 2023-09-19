---
title: ID ベースのドメイン登録の実装
description: ID ベースのドメイン登録の実装
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# ID ベースのドメイン登録の実装{#implement-identity-based-domain-registration}

1. 必須のドメイン登録を含む DRM ポリシーを作成します。
1. ドメインサーバー URL のサーバーのホストとポートを指定します。

   を [!DNL .properties] ファイル、設定：

   ```
   policy.domain.url=https://[server:port] 
   ```

1. ユーザー名とパスワードを必須にして認証を行います。

   を [!DNL .properties] ファイル、設定：

   ```
   policy.domain.anonymous=false 
   ```
