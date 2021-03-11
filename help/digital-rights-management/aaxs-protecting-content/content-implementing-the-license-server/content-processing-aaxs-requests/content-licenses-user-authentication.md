---
title: ユーザー認証
description: ユーザー認証
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# ユーザー認証{#user-authentication}

Adobeアクセス要求には、認証トークンを含めることができます。

ユーザー名/パスワード認証を使用した場合、リクエストには`AuthenticationHandler`によって生成された`AuthenticationToken`が含まれる可能性があります。 トークンにアクセスして確認するには、`RequestMessageBase.getAuthenticationToken()`を使用します。 クライアントでユーザー名/パスワードの要求を開始するには、`DRMManager.authenticate()`ActionScriptまたはiOS APIを使用します。

クライアントとサーバーがカスタム認証メカニズムを使用している場合、クライアントは他のチャネルを介して認証トークンを取得し、`DRMManager.setAuthenticationToken`ActionScript3.0 APIを使用してカスタム認証トークンを設定します。 `RequestMessageBase.getRawAuthenticationToken()`を使用して、カスタム認証トークンを取得します。 サーバーの実装は、カスタム認証トークンが有効かどうかを判断する必要があります。
