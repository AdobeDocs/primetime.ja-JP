---
title: IDベースのドメイン登録の実装
description: IDベースのドメイン登録の実装
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
