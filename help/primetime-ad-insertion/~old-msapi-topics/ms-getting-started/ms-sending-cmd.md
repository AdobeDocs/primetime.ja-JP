---
description: HTTPGETコマンドを使用して、マニフェストサーバーとやり取りします。
seo-description: HTTPGETコマンドを使用して、マニフェストサーバーとやり取りします。
seo-title: マニフェストサーバーにコマンドを送信する
title: マニフェストサーバーにコマンドを送信する
uuid: e9680563-d268-406d-87ce-1521a677e9ec
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# マニフェストサーバーにコマンドを送信{#send-a-command-to-the-manifest-server}

HTTPGETコマンドを使用して、マニフェストサーバーとやり取りします。

1. 次のパターンを使用して構築されたブートストラップURLに対して`HTTP GET`リクエストを送信します。

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **PublisherAssetIDR** が必要です。特定のコンテンツに対する発行者の一意のID。

* **コンテンツ** URLRが必要です。コンテンツM3U8ファイルのURL。マニフェストサーバーURL内で安全であるようにエンコードされたBase64。 ビットレートストリームが1つだけの場合でも、コンテンツURLはバリアントM3U8ファイルを指す必要があります。

* **クエリ** パラメーター必須のパラメーターと任意選択のパラメーターがあります。これらは、リクエストの中で最も多様な部分を構成します。 どの種類のクライアントがリクエストを行っているか、およびマニフェストサーバーに何をして欲しいかをマニフェストサーバーに伝えます。

   例：

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.m3u8?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTPリクエストとHTTPSリクエスト**

   マニフェストサーバーは、クライアントのリクエストと同じHTTPプロトコルを使用してURLを作成します。 プレーヤーが安全でないHTTP(http)リクエストを行った場合、マニフェストサーバーは、httpプロトコルを使用してマニフェストURLとAuditudeトラッキングURLを返します。 プレーヤーが安全なHTTP(https)接続、マニフェストサーバーを行うと、httpsプロトコルを使用してマニフェストURLとAuditudeトラッキングURLを返します。

   >[!NOTE]
   >
   >マニフェストサーバーは、コンテンツセグメント(.ts)とサードパーティのトラッキングビーコンのプロトコル（HTTPまたはHTTPS）を変更できません。 目的のプロトコルを設定するには、コンテンツおよびサードパーティの広告プロバイダーに問い合わせる必要があります。