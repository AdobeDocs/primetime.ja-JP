---
title: 認証トークンのタイムアウト
description: 認証トークンのタイムアウト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

アプリケーションアクセス SDK で生成されるすべてのAdobeトークンには、アプリケーションのセキュリティを保護するためのタイムアウト間隔があります。 認証トークンの有効期限が指定されている場合は、認証リクエストの処理時にAdobeアクセス SDK を使用します。 有効期限が過ぎると、認証トークンは無効になり、ユーザーはライセンスサーバーで再認証する必要があります。

認証要求について詳しくは、 *Adobeアクセス API リファレンス*.
