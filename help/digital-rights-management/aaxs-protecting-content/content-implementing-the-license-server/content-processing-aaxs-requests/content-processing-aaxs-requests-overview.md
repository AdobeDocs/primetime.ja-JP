---
seo-title: 概要
title: 概要
uuid: 870c32f5-1119-4fec-abed-25e51dd1ebe3
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# 概要{#overview}

リクエストを処理する一般的な方法は、ハンドラーの作成、リクエストの解析、応答データまたはエラーコードの設定、ハンドラーの終了です。

単一のリクエスト/応答のインタラクションを処理するために使用される基本クラスは `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`です。 クラスのインスタンスを使用して、ハンドラーを初期化し `HandlerConfiguration` ます。 `HandlerConfiguration` トランスポート資格情報、タイムスタンプの許容値、ポリシーの更新リスト、失効リストなどのサーバー構成情報を格納します。このハンドラーは、要求データを読み取り、要求を解析して、のインスタンスに渡 `RequestMessageBase`します。 呼び出し元は、リクエスト内の情報を調べ、エラーを返すか、正常な応答を返すかを決定できます(応答データを設定するためのメソッドを `RequestMessageBase` 提供するサブクラス)。

リクエストが成功した場合は、応答データを設定します。それ以外の場合は、失敗 `RequestMessageBase.setErrorData()` 時に呼び出します。 メソッドを呼び出すことで、必ず実装を終了します(ステートメントの `close()` ブロック内で呼び出すこ `close()` とをお勧めし `finally``try` ます)。 ハンドラーの呼び出し方法の例については、 `MessageHandlerBase` APIリファレンスドキュメントを参照してください。

>[!NOTE]
>
>HTTPステータスコード200 (OK)は、ハンドラーが処理するすべての要求に応答して送信する必要があります。 サーバーエラーが原因でハンドラーを作成できなかった場合、サーバーは500 （内部サーバーエラー）など、別のステータスコードで応答する可能性があります。

クライアントは、パッケージ化の際に指定されたライセンスサーバーのURLを、ライセンスサーバーに送信されるすべての要求のベースURLとして使用します。 例えば、サーバーURLを「https://licenseserver.com/path」と指定した場合、<span></span>クライアントは「<span></span>https://licenseserver.com/path/flashaccess/...」に要求を送信します。 各タイプのリクエストで使用される具体的なパスについて詳しくは、以下の節を参照してください。 ライセンスサーバーを実装する場合は、サーバーが要求の種類ごとに必要なパスに応答することを確認してください。

ライセンスリクエストには、認証トークンを含めることができます。 ユーザー名とパスワードの認証を使用した場合、リクエストにはによって `AuthenticationToken` 生成された認証が含まれ `AuthenticationHandler`ている可能性があり、SDKは、ライセンスを発行する前にトークンが有効であることを確認します。
