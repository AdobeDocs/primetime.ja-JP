---
title: クライアント要求のサンプル
description: クライアント要求のサンプル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# クライアント要求のサンプル{#sample-client-requests}

Charles Proxy や Wireshark などのツールを使用して、サンプルクライアントリクエストのライブラリを収集できます。 個別化トランスポート秘密鍵証明書を使用して、個別化サーバーの設定後にクライアント要求を取得する必要があります。 その後、これらのクライアントリクエストを ( *curl* 個別化サーバーのエンドポイントに、サーバーが正しく起動して動作していることを確認するためのツールです。 例：

```
curl https://<<yourindivserver:port>>/flashaccess/i15n/v5 -­data-binary  
@sample_client_request.bin > sample_client_response.ber
```

また、サーバー設定が変更されたり、ECI/CRL が更新されたりした後に、これらの要求を再度送信することもできます。

また、個別化トランザクションを正常に実行するように、「個別化統計」ページを適切に更新する必要があります。
