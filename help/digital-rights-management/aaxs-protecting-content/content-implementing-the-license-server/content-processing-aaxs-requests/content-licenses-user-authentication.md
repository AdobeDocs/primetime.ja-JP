---
seo-title: ユーザー認証
title: ユーザー認証
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# ユーザー認証{#user-authentication}

Adobeアクセス要求には、認証トークンを含めることができます。

ユーザー名/パスワード認証を使用した場合、リクエストには`AuthenticationHandler`によって生成された`AuthenticationToken`が含まれる可能性があります。 トークンにアクセスして確認するには、`RequestMessageBase.getAuthenticationToken()`を使用します。 クライアントでユーザー名/パスワードの要求を開始するには、`DRMManager.authenticate()`ActionScriptまたはiOS APIを使用します。

クライアントとサーバーがカスタム認証メカニズムを使用している場合、クライアントは他のチャネルを介して認証トークンを取得し、`DRMManager.setAuthenticationToken`ActionScript3.0 APIを使用してカスタム認証トークンを設定します。 `RequestMessageBase.getRawAuthenticationToken()`を使用して、カスタム認証トークンを取得します。 サーバーの実装は、カスタム認証トークンが有効かどうかを判断する必要があります。
