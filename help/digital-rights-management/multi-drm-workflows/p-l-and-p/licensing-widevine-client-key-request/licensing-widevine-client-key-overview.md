---
description: コンテンツのパッケージ化によって生成された DASH コンテンツを再生するには、 TVSDK クライアントは、キー取得ワークフローのパッケージ化プロセス中に渡されたコンテンツ復号化キーを取得する必要があります。 クライアントコンテンツの復号キーは、通常、クライアントからの 1 つ以上の HTTP/HTTPS 投稿に応じて、Widevine/PlayReady ライセンスサーバーによってクライアントに配信されます。
title: クライアントキーリクエストワークフローの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# クライアントキーリクエストワークフロー {#client-key-request-workflow-overview}

コンテンツのパッケージ化によって生成された DASH コンテンツを再生するには、 TVSDK クライアントは、キー取得ワークフローのパッケージ化プロセス中に渡されたコンテンツ復号化キーを取得する必要があります。 クライアントコンテンツの復号キーは、通常、クライアントからの 1 つ以上の HTTP/HTTPS 投稿に応じて、Widevine/PlayReady ライセンスサーバーによってクライアントに配信されます。

コンテンツ復号化キーを取得するには、PSDK クライアントが次の操作をおこなう必要があります

* コンテンツの psh ボックスを取得し、プラットフォームに提供し、キーリクエストに応じてを取得します。
* キーリクエストを HTTPPOSTを通じて適切な Widevine/PlayReady ライセンスサーバーに送信します。
* サーバーの応答をプラットフォームに渡し、応答からクライアントコンテンツの復号化キーを抽出して、コンテンツの復号化に使用します。

キーリクエストの HTTPPOSTを送信するには、コードが、ライセンスサーバーの URL と、投稿に添付する必要のある追加のデータを PSDK クライアントに渡す必要があります。 渡す URL とデータの選択は、使用する Widevine/PlayReady サービスプロバイダーによって異なります。 例えば、サービスの提供に ExpressPlay を使用する場合、適切な ExpressPlay Widevine/PlayReady ライセンスサーバー URL を渡し、送信キーにコンテンツの暗号化キーに関連付けられた ExpressPlay トークンを添付します。 適切な ExpressPlay Widevine/PlayReady ライセンスサーバーの URL は、ExpressPlay のドキュメントから入手できます。
