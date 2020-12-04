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

リクエストを処理する一般的な方法は、ハンドラーの作成、リクエストの解析、応答データまたはエラーコードの設定、およびハンドラーの終了です。

単一のリクエスト/応答のインタラクションを処理するために使用される基本クラスは`com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`です。 `HandlerConfiguration`クラスのインスタンスを使用してハンドラーが初期化されます。 `HandlerConfiguration` トランスポート資格情報、タイムスタンプの許容値、ポリシーの更新リスト、失効リストなどのサーバー構成情報を格納します。このハンドラーは、要求データを読み取り、要求を解析して、のインスタンスに渡 `RequestMessageBase`します。呼び出し元は、要求内の情報を調べ、エラーを返すか、応答を成功させるかを判断できる（`RequestMessageBase`のサブクラスが応答データを設定する方法を提供する）。

リクエストが成功した場合は、応答データを設定します。それ以外の場合は、失敗時に`RequestMessageBase.setErrorData()`を呼び出します。 必ず`close()`メソッドを呼び出して実装を終了してください（`try`ステートメントの`finally`ブロック内で`close()`を呼び出すことをお勧めします）。 ハンドラーの呼び出し方法の例については、`MessageHandlerBase` APIリファレンスドキュメントを参照してください。

>[!NOTE]
>
>HTTPステータスコード200 (OK)は、ハンドラーが処理するすべての要求に応答して送信する必要があります。 サーバーエラーが原因でハンドラーを作成できなかった場合、サーバーは500 （内部サーバーエラー）など、別のステータスコードで応答する可能性があります。

クライアントは、パッケージ化の際に指定されたライセンスサーバーのURLを、ライセンスサーバーに送信されるすべての要求のベースURLとして使用します。 例えば、サーバーURLを&quot;ht<span></span>tps://licenseserver.com/path&quot;と指定した場合、クライアントは要求を&quot;ht<span></span>tps://licenseserver.com/path/flashaccess/...&quot;に送信します。 各タイプのリクエストで使用される具体的なパスについて詳しくは、以下の節を参照してください。 ライセンスサーバーを実装する場合は、サーバーが要求の種類ごとに必要なパスに応答することを確認してください。

ライセンスリクエストには、認証トークンを含めることができます。 ユーザー名/パスワード認証を使用した場合、リクエストには`AuthenticationHandler`によって生成された`AuthenticationToken`が含まれている可能性があり、SDKは、ライセンスを発行する前にトークンが有効であることを確認します。
