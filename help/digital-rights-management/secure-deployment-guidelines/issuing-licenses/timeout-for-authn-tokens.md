---
description: Adobe PrimetimeDRM SDKによって生成されるすべての認証トークンには、アプリケーションのセキュリティを保護するためのタイムアウト間隔があります。
title: 認証トークンのタイムアウト
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

Adobe PrimetimeDRM SDKによって生成されるすべての認証トークンには、アプリケーションのセキュリティを保護するためのタイムアウト間隔があります。

認証トークンの有効期限は、認証要求を処理する際にPrimetime DRM SDKを使用して指定されます。 有効期限が切れると、トークンは無効になり、ユーザーはライセンスサーバーで再認証する必要があります。

認証要求について詳しくは、[AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html)を参照してください。
