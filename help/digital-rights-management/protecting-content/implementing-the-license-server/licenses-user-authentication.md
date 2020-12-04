---
seo-title: ユーザー認証
title: ユーザー認証
uuid: 5cbd76b9-ff64-4a4b-8cfd-54f05c04eaa3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# ユーザー認証{#user-authentication}

Adobe PrimetimeのDRMリクエストには、認証トークンを含めることができます。

ユーザー名/パスワード認証を使用した場合は、`AuthenticationHandler`によって生成された`AuthenticationToken`がリクエストに含まれる可能性があります。 トークンにアクセスして確認する場合は、`RequestMessageBase.getAuthenticationToken()`を使用する必要があります。 クライアントでユーザー名/パスワードの要求を開始するには、`DRMManager.authenticate()`ActionScriptまたはiOS APIを使用します。

クライアントおよびサーバーがカスタム認証メカニズムを使用する場合、クライアントは他のチャネルを介して認証トークンを取得し、`DRMManager.setAuthenticationToken`ActionScript3.0 APIを使用してカスタム認証トークンを設定します。 `RequestMessageBase.getRawAuthenticationToken()`を使用して、カスタム認証トークンを取得します。 サーバーの実装によって、カスタム認証トークンが有効かどうかが決まります。
