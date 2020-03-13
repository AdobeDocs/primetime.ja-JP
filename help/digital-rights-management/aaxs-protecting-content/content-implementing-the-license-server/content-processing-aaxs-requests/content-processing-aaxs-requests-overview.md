---
seo-title: 概要
title: 概要
uuid: 870c32f5-1119-4fec-abed-25e51dd1ebe3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 概要{#overview}

リクエストを処理する一般的な方法は、ハンドラーを作成し、リクエストを解析し、応答データまたはエラーコードを設定して、ハンドラーを閉じることです。

単一のリクエスト/応答のインタラクションを処理するために使用される基本クラスはで `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`す。 クラスのインスタンス `HandlerConfiguration` を使用してハンドラーが初期化されます。 `HandlerConfiguration` は、トランスポート資格情報、タイムスタンプの許容値、ポリシーの更新リスト、失効リストなどのサーバー構成情報を格納します。ハンドラーは、要求データを読み取り、要求を解析して、のインスタンスに取り込みま `RequestMessageBase`す。 呼び出し元は、リクエスト内の情報を調べ、エラーを返すか、成功した応答を返すかを決定できます(のサブクラスは、応答デ `RequestMessageBase` ータを設定する方法を提供します)。

リクエストが成功した場合は、応答データを設定します。それ以外の場合は、失 `RequestMessageBase.setErrorData()` 敗時に呼び出します。 メソッドを呼び出すことで、必ず実 `close()` 装を終了します(ステートメ `close()` ントのブロック内で呼び出す `finally` ことをお勧 `try` めします)。 ハンドラーの呼び出し方法の例については、 `MessageHandlerBase` APIリファレンスドキュメントを参照してください。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>HTTPステータスコード200 (OK)は、ハンドラーで処理されるすべての要求に応じて送信されます。 サーバーエラーが原因でハンドラーを作成できなかった場合、サーバーは500 （内部サーバーエラー）などの別のステータスコードで応答する可能性があります。

クライアントは、パッケージ化時に指定されたライセンスサーバのURLを、ライセンスサーバに送信されるすべての要求のベースURLとして使用します。 例えば、サーバーURLが「<span></span>https://licenseserver.com/path」と指定されている場合、クライアントは「https://licenseserver.com/path/flashaccess/...」<span></span>に要求を送信します。 リクエストの各タイプで使用される具体的なパスについて詳しくは、以下の節を参照してください。 ライセンスサーバーを実装する場合は、各要求タイプに必要なパスにサーバーが応答することを確認します。

ライセンス要求には、認証トークンを含めることができます。 ユーザー名/パスワード認証が使用された場合、リクエストには、によって生成されたものが含まれてい `AuthenticationToken` る可能性があり、SDKは、ライ `AuthenticationHandler`センスを発行する前にトークンが有効であることを確認します。
