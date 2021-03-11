---
title: 匿名ドメイン登録の実装
description: 匿名ドメイン登録の実装
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# 匿名ドメイン登録{#implement-anonymous-domain-registration}の実装

1. ドメイン登録が必要であることを指定するDRMポリシーを作成します。
1. ドメインサーバーのURLを次のように指定します。

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. 匿名認証を必須にします。

   [!DNL .properties]ファイルに次を設定します。

   ```
   policy.domain.anonymous=true 
   ```
