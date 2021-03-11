---
title: 認証トークンのタイムアウト
description: 認証トークンのタイムアウト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

AdobeアクセスSDKによって生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔があります。 認証トークンの有効期限は、認証要求を処理する際に、AdobeアクセスSDKを使用して指定します。 有効期限が過ぎると、認証トークンは無効になり、ユーザーはライセンスサーバーで再認証する必要があります。

認証要求について詳しくは、『*AdobeアクセスAPIリファレンス*』の「AuthenticationHandler」を参照してください。
