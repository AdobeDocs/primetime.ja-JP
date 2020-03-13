---
seo-title: クライアントリクエストの例
title: クライアントリクエストの例
uuid: 330d5e3c-1711-4375-bd11-e7702f0cde31
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# クライアントリクエストの例{#sample-client-requests}

Charles ProxyやWiresharkなどのツールを使用して、サンプルのクライアントリクエストのライブラリを収集できます。 個別化サーバーの設定後、個別化トランスポートの秘密鍵証明書を使用して、クライアント要求を取得する必要があります。 その後、( *curl* または他のツールを使用して)これらのクライアント要求を個別化サーバーのエンドポイントに送信し、サーバーが正常に起動し、動作していることを確認できます。 例：

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

また、サーバー設定の変更やECI / CRLの更新が行われた後で、これらの要求を再度送信することもできます。

また、個別化トランザクションを正常に実行して、個別化の統計ページを適切に更新する必要があります。
