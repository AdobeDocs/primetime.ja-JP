---
seo-title: クライアントリクエストの例
title: クライアントリクエストの例
uuid: 330d5e3c-1711-4375-bd11-e7702f0cde31
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---


# クライアントリクエストの例{#sample-client-requests}

Charles ProxyやWiresharkなどのツールを使用して、サンプルクライアントリクエストのライブラリを収集できます。 個別化サーバーが設定されたら、個別化トランスポート秘密鍵証明書を使用して、クライアント要求を取得する必要があります。 その後、（*curl*&#x200B;または他のツールを介して）これらのクライアント要求を個別化サーバーのエンドポイントに送信し、サーバーが正常に起動して実行されていることを確認できます。 例：

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

サーバー設定が変更されたり、ECI/CRLが更新された場合は、これらの要求を再度送信することもできます。

個別化の統計ページを適切に更新し、個別化トランザクションを正常に完了させる必要もあります。
