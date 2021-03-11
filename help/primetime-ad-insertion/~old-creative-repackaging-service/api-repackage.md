---
description: CRS再パッケージ化APIを使用して、非HLS広告クリエイティブを事前にトランスコードできるので、HLSバージョンを実行する必要がある場合にHLSバージョンを利用でき、ジャストインタイム(JIT)再パッケージ化に伴う2 ～ 4分の遅延を解消できます。
title: 再パッケージ化API
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---


# APIの再パッケージ化{#repackaging-api}

CRS再パッケージ化APIを使用して、非HLS広告クリエイティブを事前にトランスコードできるので、HLSバージョンを実行する必要がある場合にHLSバージョンを利用でき、ジャストインタイム(JIT)再パッケージ化に伴う2 ～ 4分の遅延を解消できます。

## HTTP要求{#section_F616F5722F0B4AB7939EE2ECBEDDB297}

HTTPPOSTコマンドを指定したURLに送信して、トランスコードする広告クリエイティブと使用するオプションをCRSに通知します。 応答コードは、成功または失敗とその他の情報をレポートします。

この要求にはユーザ名とパスワードが必要です。 これらは、Adobeのテクニカルアカウントマネージャーから入手できます。 認証について詳しくは、Adobe Primetime有効化担当者にお問い合わせください。

トランスコードリクエストをCRSに送信するには、次のようにHTTPメッセージを送信します。

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **方法 —** `POST`

* **認証 —** `Digest`

* **ヘッダー —** `Content-Type: text/xml`

* **次の例のようなBody -** XML

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

Body内の`RepackageList`ブロックには、1 ～ 300個の`Repackage`ブロックを含めることができます。 Body内の`Repackage`ブロックの数が300を超える場合、HTTP要求は次のエラーで失敗します。

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


`Repackage`ブロック内の必須パラメーターと任意選択パラメーターは次のとおりです。

* **`AdSystem`** （必須） — ソース広告サーバー( `Auditude`、、な `FreeWheel`ど) `Apad.tv`。これは、VAST要素`AdSystem`に対応するstring値です。

* **`AdId`** （必須） — リクエストで指定されたサードパーティ広告サーバーの識別子です。VAST応答の`Ad`要素の`id`属性に対応します。

* **`CreativeURL`** （必須） — トランスコードする広告クリエイティブの場所(URI)。これはVAST `MediaFile`要素に対応します。

* `CreativeID` （オプション） — 広告エクスペリエンスの一部として含める広告クリエイティブの識別子。
* **`Zone`** （必須） — アカウントのゾーンID（テクニカルアカウントマネージャーから入手）これは、Auditudeプラットフォーム`publisher_site_id`の設定に対応する数値です。

* **`Format`** （オプション） — CRSが広告クリエイティブをトランスコードする方法を制御するパラメーター。

   * `clientside` - TVSDKがCDNとの通信に使用するURLとの互換性がある出力を生成します。
   >[!IMPORTANT]
   >
   >再パッケージ化された広告をクライアント側Ad Insertionと互換性を持たせる場合は、このパラメーターを指定する必要があります。 これを指定しない場合、再パッケージ化された広告は、サーバー側Ad Insertionとのみ互換性があります。

   * `hls` - HLS互換のトランスコードされた広告クリエイティブを生成します。
   * `dash` - DASH互換のトランスコードされた広告クリエイティブを生成します。
   * `id3`  — トランスコードされた広告クリエイティブにID3時間指定メタデータタグを挿入します。
   * `targetdur`  — トランスコードされた広告クリエイティブのセグメントの時間（秒）。初期設定は`targetdur=4`です。 この値は、ターゲット期間タグの`<s>`のマニフェストで指定されている値に対応する必要があります。`#EXT-X-TARGETDURATION:<s>`.

   >[!NOTE]
   >
   >DASH互換のアセットは、Adobe Primetime広告挿入と互換性がありません。

>[!IMPORTANT]
>
>再生をスムーズにするには、コンテンツのチャンク時間の長さに合わせて`targetdur`を設定します。

## HTTP応答{#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRSは、次のステータスコードのいずれかでリクエストに応答します。

* **HTTP 202**  — 受け入れられます（空の本文を含む）。これは成功を示します。 CRSは、トランスコードされた広告をCDNサーバにアップロードします。
* **HTTP 400**  — 無効な要求です。ポストされたXMLが無効です。
* **HTTP 500**  — 内部サーバーエラー。サーバーで内部の問題が発生しました（例えば、サーバーがデータベースに接続できなかった）。

## SSAIまたはCSAI用のアセットのトランスコード前{#section_098888BB74FD4DC1AD0BD507B2A48318}

再パッケージ化APIを使用して、将来のSSAIまたはCSAIイベントを事前にトランスコードできます。 アセットが将来SSAIで使用される予定の場合は、POST呼び出しのすべてのパラメーターが一意であることを確認してください。 パラメーターは次のとおりです。AdSystem、AdId、CreativeURL、Zone、Format。 このパラメーターのセットに相違がある場合は、SSAIに対する新しいトランスコードリクエストが発生します。

CSAIで使用される将来的なアセットの場合、アセットの一意性はゾーンとCreativeURLに依存します。 AdSystemとAdIdは、異なるトランスコードされたアセットを生成しません。これらのアセットはクライアントが使用できます。
