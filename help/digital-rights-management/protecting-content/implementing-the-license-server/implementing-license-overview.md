---
seo-title: ライセンスサーバの概要
title: ライセンスサーバの概要
uuid: 8c62376b-b159-4297-9322-75d62947e84e
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# 概要{#license-server-overview}

クライアントにライセンスを発行する前に、Adobe PrimetimeDRMライセンスサーバーを展開する必要があります。 ライセンスサーバーは、Primetime DRM SDKを使用して多数のタスクを実行します。

License Serverを実装するには：

* ユーザー名/パスワード認証がサポートされている場合は、認証要求を処理します。
* ライセンス要求の処理
* Process Get Server Version requests — すべてのサーバーで、このタイプのリクエストのサポートを実装する必要があります。
* ドメイン登録要求の処理 — ドメインサーバーを実装する場合にのみ必要です。
* ドメイン登録解除要求を処理する — ドメインサーバーを実装する場合にのみ必要です。
* プロセス同期 — ライセンスで同期の要件が指定されている場合にのみ必要です。

また、サーバは、ユーザの認証、表示コンテンツの認証を行う権限のあるユーザの決定、およびオプションでライセンスの使用の追跡を行うビジネスロジックを提供する必要があります。

Java APIについて詳しくは、*Adobe PrimetimeDRM APIリファレンス*&#x200B;を参照してください。
