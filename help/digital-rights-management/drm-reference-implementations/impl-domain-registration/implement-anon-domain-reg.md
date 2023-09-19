---
title: 匿名ドメイン登録の実装
description: 匿名ドメイン登録の実装
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# 匿名ドメイン登録の実装{#implement-anonymous-domain-registration}

1. ドメイン登録が必要であることを指定する DRM ポリシーを作成します。
1. ドメインサーバー URL を次のように指定します。

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. 匿名認証を必須にします。

   を [!DNL .properties] ファイル、設定：

   ```
   policy.domain.anonymous=true 
   ```
