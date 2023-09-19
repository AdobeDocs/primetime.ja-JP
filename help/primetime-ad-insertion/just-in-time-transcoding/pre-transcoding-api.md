---
title: 事前トランスコード API
description: ジャストインタイム再パッケージ化 API を使用して、事前に広告クリエイティブをトランスコードできるので、必要に応じてコンテンツ互換バージョンを利用でき、ジャストインタイム (JIT) 再パッケージに伴う 2 ～ 4 分の遅延を解消できます。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# API の事前トランスコードと再パッケージ化 {#pre-transcoding-api}

PrimetimeAd Insertionは、大規模な直売イベントなど、クリエイティブ URL があらかじめわかっている状況での事前トランスコード API を提供します。  これにより、ジャストインタイムトランスコーディングに関連する 2 ～ 4 分の遅延がなくなります。

## HTTP リクエスト {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

HTTPPOSTコマンドを指定の URL に送信して、トランスコードする広告クリエイティブと使用するオプションを CRS に伝えます。 応答コードは、成功または失敗とその他の情報をレポートします。

このリクエストには、ユーザー名とパスワードが必要です。 これらは、担当のテクニカルアカウントマネージャーからAdobeで入手できます。 認証について詳しくは、Adobe Primetimeイネーブルメント担当者にお問い合わせください。

トランスコードリクエストを CRS に送信するには、次のように HTTP メッセージを送信します。

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **メソッド —** `POST`

* **認証 —** `Digest`

* **ヘッダー —** `Content-Type: text/xml`

* **本文 —** XML は次の例のようになります。

  ```xml
  <RepackageList>
      <Repackage>
          <AdSystem>Auditude</AdSystem>
          <AdID>AUD1</AdID>
          <CreativeID>AUD-CR1</CreativeID>
          <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
          <Zone>3</Zone>
      </Repackage>
      <Repackage>
          <AdSystem>Auditude</AdSystem>
          <AdID>AUD2</AdID>
          <CreativeID>AUD-CR1</CreativeID>
          <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
          <Format>id3 targetdur=5</Format>
          <Zone>3</Zone>
      </Repackage>
  </RepackageList>
  ```

The `RepackageList` 本文のブロックには、1 ～ 300 を含めることができます `Repackage` ブロック。 次の項目に対して `Repackage` Body 内のブロックが 300 を超える場合、HTTP リクエストは次のエラーで失敗します。

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


必須およびオプションのパラメーター ( `Repackage` ブロックは次のようになります。

* **`AdSystem`** （必須） — ソース広告サーバー。例： `Auditude`, `FreeWheel`, `Apad.tv`. これは VAST 要素に対応する string 値です `AdSystem`.

* **`AdId`** （必須） — リクエストで指定されたサードパーティの広告サーバーの識別子です。 これは、 `id` の属性 `Ad` 要素を VAST 応答に含める必要があります。

* **`CreativeURL`** （必須） — トランスコードする広告クリエイティブの場所 (URI)。 これは、VAST `MediaFile` 要素を選択します。

* `CreativeID` （オプション） — 広告エクスペリエンスの一部として含める広告クリエイティブの識別子。
* **`Zone`** （必須） — アカウントのゾーン ID（テクニカルアカウントマネージャーから取得）。 これは、Auditudeプラットフォームに対応する数値です `publisher_site_id` 設定。

* **`Format`** （オプション） - CRS が広告クリエイティブをトランスコードする方法を制御するパラメーター。

   * `clientside` - TVSDK が CDN との通信に使用する URL と互換性のある出力を生成します。

  >[!IMPORTANT]
  >
  >再パッケージ化された広告をクライアント側のAd Insertionと互換性を持たせる場合は、このパラメーターを指定する必要があります。 指定しない場合、再パッケージ化された広告は Server SideAd Insertionとのみ互換性があります。

   * `hls` - HLS 互換のトランスコードされた広告クリエイティブを生成します。
   * `dash` - DASH 互換のトランスコードされた広告クリエイティブを生成します。
   * `id3`  — トランスコードされた広告クリエイティブに ID3 時間指定メタデータタグを挿入します。
   * `targetdur`  — トランスコードされた広告クリエイティブのセグメントの時間（秒）。 デフォルトはです。 `targetdur=4`. この値は、 `<s>` ターゲット期間タグ内： `#EXT-X-TARGETDURATION:<s>`.

  >[!NOTE]
  >
  >DASH 互換のアセットは、Adobe Primetime広告挿入と互換性がありません。

>[!IMPORTANT]
>
>再生をスムーズにするには、 `targetdur` コンテンツチャンクの期間を一致させる。

## HTTP 応答 {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRS は、次のいずれかのステータスコードでリクエストに応答します。

* **HTTP 202**  — 許可済み（空の本文を含む） これは成功を示します。 CRS は、トランスコードされた広告を CDN サーバーにアップロードします。
* **HTTP 400**  — リクエストが正しくありません。 投稿された XML が無効です。
* **HTTP 500**  — 内部サーバーエラー。 サーバーで内部問題が発生しました（例えば、サーバーがデータベースに接続できませんでした）。

## SSAI または CSAI 用のアセットの事前トランスコード {#section_098888BB74FD4DC1AD0BD507B2A48318}

再パッケージ化 API を使用して、今後の SSAI または CSAI イベントを事前にトランスコードできます。 アセットを将来 SSAI で使用する場合は、アセット呼び出しのすべてのパラメーターが一意であることをPOSTしてください。 パラメーターは、AdSystem、AdId、CreativeURL、Zone、Format です。 このパラメータのセットに違いがある場合は、SSAI の新しいトランスコードリクエストが発生します。

今後 CSAI で使用されるアセットの場合、アセットの一意性は Zone と CreativeURL に依存します。 AdSystem と AdId は異なるトランスコードされたアセットにはならず、クライアントが使用できます。
