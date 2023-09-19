---
title: ユーザー認証
description: ユーザー認証
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# ユーザー認証{#user-authentication}

Adobeアクセスリクエストには、認証トークンを含めることができます。

ユーザー名/パスワード認証を使用した場合、リクエストには `AuthenticationToken` 生成元 `AuthenticationHandler`. トークンにアクセスして検証するには、 `RequestMessageBase.getAuthenticationToken()`. クライアントでユーザー名/パスワードリクエストを開始するには、 `DRMManager.authenticate()` ActionScriptまたはiOS API。

クライアントとサーバーがカスタム認証メカニズムを使用している場合、クライアントは他のチャネルを介して認証トークンを取得し、 `DRMManager.setAuthenticationToken` ActionScript3.0 API。 用途 `RequestMessageBase.getRawAuthenticationToken()` をクリックして、カスタム認証トークンを取得します。 サーバーの実装は、カスタム認証トークンが有効かどうかを判断する役割を果たします。
