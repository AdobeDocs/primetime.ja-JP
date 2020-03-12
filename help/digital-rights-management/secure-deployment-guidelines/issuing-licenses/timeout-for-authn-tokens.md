---
description: Adobe Primetime DRM SDKによって生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔があります。
seo-description: Adobe Primetime DRM SDKによって生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔があります。
seo-title: 認証トークンのタイムアウト
title: 認証トークンのタイムアウト
uuid: 2c2b0dad-0979-4d49-b109-2700ceb4d722
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

Adobe Primetime DRM SDKによって生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔があります。

認証トークンの有効期限は、認証要求を処理する際にPrimetime DRM SDKを使用して指定されます。 有効期限が切れると、トークンは無効になり、ユーザーはライセンスサーバーを使用して再度認証する必要があります。

認証要求について詳しくは、AuthenticationHandlerを参照して [ください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html)。
