---
seo-title: 認証要求の処理
title: 認証要求の処理
uuid: abcb9cf6-668e-405c-9659-9ed1bcc33024
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 認証要求の処理 {#handle-authentication-requests}

このク `AuthenticationHandler` ラスは、認証要求を処理するために使用されます。 ユーザー名とパスワードの認証にのみ使用されます。

認証トークンを生成する際は、トークンの有効期限を指定する必要があります。 カスタムプロパティもトークンに含めることができます。 設定した場合、認証トークンが後続の要求で送信されると、これらのプロパティがサーバーに表示されます。 カスタム認 [証トークンの処理について詳しくは](../../protecting-content/implementing-the-license-server/handling-license-reqs/license-handling-classes.md) 、「ライセンス要求の処理」を参照してください。

ハンドラーは認証要求を読み取り、が呼び出されると要求メッセージ `parseRequest()` を解析します。 サーバー実装は、リクエスト内のユーザー資格情報を調べ、資格情報が有効な場合、を呼び出してオブジェクト `AuthenticationToken` を生成しま `getRequest().generateAuthToken()`す。 が以前 `AuthenticationRequestMessage.generateAuthToken()` に呼び出されなか `close()`った場合は、認証失敗エラーコードが送信されます。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.authentication.AuthenticationRequestMessage`
* クライアントとサーバの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバURL:+ &quot; [!DNL /flashaccess/authn/v4]&quot; プロトコルバージョン3がクライアントまたはサーバーでサポートされる最大値である場合、Adobe Primetime DRMクライアントは認証要求を「メタデータのライセンスサーバーURL」 + 「」に送信し [!DNL /flashaccess/authn/v3]ます。 それ以外の場合、認証要求は「メタデータのライセンスサーバURL」 + 「」に送信され [!DNL /flashaccess/authn/v1]ます

