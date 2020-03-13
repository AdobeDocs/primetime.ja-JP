---
description: HTTP GETコマンドを使用して、マニフェストサーバーとやり取りします。
seo-description: HTTP GETコマンドを使用して、マニフェストサーバーとやり取りします。
seo-title: マニフェストサーバーへのコマンドの送信
title: マニフェストサーバーへのコマンドの送信
uuid: e9680563-d268-406d-87ce-1521a677e9ec
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# マニフェストサーバーへのコマンドの送信 {#send-a-command-to-the-manifest-server}

HTTP GETコマンドを使用して、マニフェストサーバーとやり取りします。

1. 次のパターン `HTTP GET` を使用して構築されたブートストラップURLに対する要求を送信します。

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.m3u8
    ?{query parameters}
   ```

* **PublisherAssetID** 。 特定のコンテンツに対する発行者の一意のID。

* **コンテンツURL** 。 マニフェストサーバーURL内で安全であるようにエンコードされたM3U8ファイルのURL。 ビットレートストリームが1つだけの場合でも、コンテンツURLはバリアントM3U8ファイルを参照する必要があります。

* **クエリパラメータ** ：必須のパラメータも、オプションのパラメータもあります。 これらは、リクエストの最も多様な部分です。 マニフェストサーバーに対して、どの種類のクライアントが要求を行っているか、およびマニフェストサーバーに何を行いたいかを伝えます。

   例：

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.m3u8?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTPリクエストとHTTPSリクエスト**

   マニフェストサーバーは、クライアントの要求と同じHTTPプロトコルを使用してURLを作成します。 プレーヤーがセキュリティで保護されていないHTTP(http)リクエストを行った場合、マニフェストサーバーは、httpプロトコルを使用してマニフェストURLとAuditude追跡URLを返します。 プレーヤーが安全なHTTP(https)接続、マニフェストサーバーを作成した場合、マニフェストURLと、httpsプロトコルを使用したAuditude追跡URLを返します。

   >[!NOTE]
   >
   >マニフェストサーバーは、コンテンツセグメント(.ts)とサードパーティのトラッキングビーコンのプロトコル（HTTPまたはHTTPS）を変更できません。 必要なプロトコルを設定するには、コンテンツおよびサードパーティの広告プロバイダーに問い合わせる必要があります。