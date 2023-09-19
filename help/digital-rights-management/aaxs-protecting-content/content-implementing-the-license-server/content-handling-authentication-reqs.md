---
title: 認証リクエストの処理
description: 認証リクエストの処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# 認証リクエストの処理{#handling-authentication-requests}

The `AuthenticationHandler` クラスは、認証リクエストを処理するために使用されます。 ユーザー名/パスワード認証にのみ使用されます。

認証トークンを生成する際には、トークンの有効期限を指定する必要があります。 カスタムプロパティをトークンに含めることもできます。 設定した場合、以降のリクエストで認証トークンが送信されたときに、これらのプロパティがサーバーに対して表示されます。 詳しくは、 [ライセンスリクエストの処理](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md) カスタム認証トークンの処理に関する情報を参照してください。

ハンドラーは、認証要求を読み取り、次の場合に要求メッセージを解析します。 `parseRequest()` が呼び出されます。 サーバー実装は、リクエスト内のユーザー資格情報を調べ、資格情報が有効な場合はを生成します。 `AuthenticationToken` を呼び出すことで、 `getRequest().generateAuthToken()`. 次の場合 `AuthenticationRequestMessage.generateAuthToken()` が次の値より前に呼び出されていません： `close()`に設定すると、認証失敗エラーコードが送信されます。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「License Server URL in metadata: + &quot;/flashaccess/authn/v4」になります。 Adobeバージョン 3 がクライアントまたはサーバーでサポートされる最大値の場合、プロトコルアクセスクライアントは認証要求を「メタデータのライセンスサーバー URL」+「/flashaccess/authn/v3」に送信します。 それ以外の場合は、認証要求が「メタデータのライセンスサーバー URL」 + 「/flashaccess/authn/v1」に送信されます。
