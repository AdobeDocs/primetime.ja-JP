---
seo-title: 認証トークンのタイムアウト
title: 認証トークンのタイムアウト
uuid: 41b0fbf5-a567-4118-bec1-c05e6e0b6d1f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

Adobe Access SDKで生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔が設定されています。 認証トークンの有効期限は、認証要求を処理する際にAdobe Access SDKを使用して指定されます。 有効期限が過ぎると、認証トークンは無効になり、ユーザーはライセンスサーバーを再認証する必要があります。

認証要求について詳しくは、 *Adobe Access APIリファレンスの「AuthenticationHandler」を参照してください*。
