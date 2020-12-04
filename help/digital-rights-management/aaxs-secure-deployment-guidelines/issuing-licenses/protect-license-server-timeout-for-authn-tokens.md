---
seo-title: 認証トークンのタイムアウト
title: 認証トークンのタイムアウト
uuid: 41b0fbf5-a567-4118-bec1-c05e6e0b6d1f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

AdobeアクセスSDKによって生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔があります。 認証トークンの有効期限は、認証要求を処理する際に、AdobeアクセスSDKを使用して指定します。 有効期限が過ぎると、認証トークンは無効になり、ユーザーはライセンスサーバーで再認証する必要があります。

認証要求について詳しくは、『*AdobeアクセスAPIリファレンス*』の「AuthenticationHandler」を参照してください。
