---
seo-title: 匿名ドメイン登録の実装
title: 匿名ドメイン登録の実装
uuid: 330d32fd-8c23-40f9-949b-635e5a9acc86
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
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
