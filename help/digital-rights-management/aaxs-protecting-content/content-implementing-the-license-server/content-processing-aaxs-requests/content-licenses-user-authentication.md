---
seo-title: ユーザー認証
title: ユーザー認証
uuid: 191964eb-cd68-47a6-8214-aec01f993df4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ユーザー認証{#user-authentication}

Adobe Accessリクエストには、認証トークンを含めることができます。

ユーザー名/パスワード認証が使用された場合、リクエストには、 `AuthenticationToken``AuthenticationHandler`トークンにアクセスして確認するには、を使用しま `RequestMessageBase.getAuthenticationToken()`す。 クライアント上でユーザー名/パスワードのリクエストを開始するには、 `DRMManager.authenticate()` ActionScriptまたはiOS APIを使用します。

クライアントとサーバーがカスタム認証メカニズムを使用している場合、クライアントは他のチャネルを通じて認証トークンを取得し、 `DRMManager.setAuthenticationToken` ActionScript 3.0 APIを使用してカスタム認証トークンを設定します。 を使用し `RequestMessageBase.getRawAuthenticationToken()` て、カスタム認証トークンを取得します。 サーバーの実装は、カスタム認証トークンが有効かどうかを判断する必要があります。
