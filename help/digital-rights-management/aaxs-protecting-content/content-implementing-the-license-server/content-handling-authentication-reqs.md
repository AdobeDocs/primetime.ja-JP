---
title: 認証要求の処理
description: 認証要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---


# 認証要求の処理{#handling-authentication-requests}

`AuthenticationHandler`クラスは、認証要求を処理するために使用されます。 これは、ユーザー名とパスワードの認証にのみ使用されます。

認証トークンを生成する際は、トークンの有効期限を指定する必要があります。 カスタムプロパティは、トークンに含めることもできます。 設定した場合、認証トークンが以降の要求で送信されるときに、これらのプロパティがサーバーに対して表示されます。 カスタム認証トークンの処理については、[ライセンス要求の処理](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-handling-license-reqs.md)を参照してください。

ハンドラーは認証要求を読み取り、`parseRequest()`が呼び出されると要求メッセージを解析します。 サーバー実装は、リクエスト内のユーザー資格情報を調べ、資格情報が有効な場合は、`getRequest().generateAuthToken()`を呼び出して`AuthenticationToken`オブジェクトを生成します。 `AuthenticationRequestMessage.generateAuthToken()`が`close()`の前に呼び出されない場合は、認証失敗エラーコードが送信されます。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバーURL:+ &quot;/flashaccess/authn/v4&quot; プロトコルバージョン3がクライアントまたはサーバーでサポートされる最大数である場合、Adobeアクセスクライアントは認証要求を「License Server URL in metadata」 + &quot;/flashaccess/authn/v3&quot;に送信します。 それ以外の場合は、認証要求は「メタデータのライセンスサーバーのURL」 + 「/flashaccess/authn/v1」に送信されます。

