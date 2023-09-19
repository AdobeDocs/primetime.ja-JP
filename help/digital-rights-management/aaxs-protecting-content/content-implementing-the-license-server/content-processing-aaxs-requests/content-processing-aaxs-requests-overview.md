---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 概要{#overview}

リクエストの処理に関する一般的なアプローチは、ハンドラーの作成、リクエストの解析、応答データまたはエラーコードの設定、およびハンドラーのクローズです。

単一のリクエスト/応答のインタラクションを処理するために使用される基本クラスは、 `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. のインスタンス `HandlerConfiguration` クラスは、ハンドラーを初期化するために使用されます。 `HandlerConfiguration` 転送資格情報、タイムスタンプの許容値、ポリシーの更新リスト、失効リストを含むサーバーの構成情報を格納します。ハンドラーは、要求データを読み取り、要求を解析して、 `RequestMessageBase`. 呼び出し元は、リクエスト内の情報を調べ、エラーを返すか、正常な応答を返すかを決定できます ( `RequestMessageBase` 応答データを設定する方法を提供する。)

リクエストが成功した場合は、応答データを設定します。成功しなかった場合は、を呼び出します。 `RequestMessageBase.setErrorData()` 失敗した場合。 常に、 `close()` メソッド ( `close()` 呼び出される `finally` ブロック `try` ステートメント )。 詳しくは、 `MessageHandlerBase` API リファレンスドキュメントを参照してください。

>[!NOTE]
>
>HTTP ステータスコード 200(OK) は、ハンドラーによって処理されるすべての要求に応じて送信される必要があります。 サーバーエラーが原因でハンドラーを作成できなかった場合、サーバーは 500（内部サーバーエラー）など別のステータスコードで応答する場合があります。

クライアントは、パッケージ化時に指定されたライセンスサーバ URL を、ライセンスサーバに送信されるすべての要求のベース URL として使用します。 例えば、サーバー URL が「ht」と指定されている場合、<span></span>tps://licenseserver.com/path」の場合、クライアントは要求を「ht」に送信します。<span></span>tps://licenseserver.com/path/flashaccess/...&quot;...... 各タイプのリクエストで使用される特定のパスの詳細については、次の節を参照してください。 ライセンスサーバーを実装する場合は、サーバーが要求のタイプごとに必要なパスに応答していることを確認してください。

ライセンスリクエストには、認証トークンを含めることができます。 ユーザー名/パスワード認証を使用した場合、リクエストには `AuthenticationToken` 生成元 `AuthenticationHandler`、および SDK は、ライセンスを発行する前に、トークンが有効であることを確認します。
