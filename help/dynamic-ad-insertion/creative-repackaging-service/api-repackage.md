---
description: CRS再パッケージ化APIを使用して、非HLS広告クリエイティブを事前にトランスコードできるので、HLSバージョンを実行する必要が生じたときにHLSバージョンを利用でき、ジャストインタイム(JIT)の再パッケージ化に伴う2 ～ 4分の遅延を解消できます。
seo-description: CRS再パッケージ化APIを使用して、非HLS広告クリエイティブを事前にトランスコードできるので、HLSバージョンを実行する必要が生じたときにHLSバージョンを利用でき、ジャストインタイム(JIT)の再パッケージ化に伴う2 ～ 4分の遅延を解消できます。
seo-title: 再パッケージAPI
title: 再パッケージAPI
uuid: 03cd2428-510a-4b99-8496-059a48d5abba
translation-type: tm+mt
source-git-commit: 5c026bfc678bafc08f93ad056823e36fd77a8a25

---


# 再パッケージAPI {#repackaging-api}

CRS再パッケージ化APIを使用して、非HLS広告クリエイティブを事前にトランスコードできるので、HLSバージョンを実行する必要が生じたときにHLSバージョンを利用でき、ジャストインタイム(JIT)の再パッケージ化に伴う2 ～ 4分の遅延を解消できます。

## HTTPリクエスト {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

HTTP POSTコマンドを指定したURLに送信して、トランスコードする広告クリエイティブと、使用するオプションをCRSに通知します。 応答コードは、成功または失敗およびその他の情報を報告します。

この要求にはユーザ名とパスワードが必要です。 これらは、アドビのテクニカルアカウントマネージャーから入手できます。 認証に関する情報が必要な場合は、Adobe Primetime Enablementの担当者にお問い合わせください。

CRSにトランスコードリクエストを送信するには、次のようにHTTPメッセージを送信します。

* **URL -** [https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **メソッド —**`POST`

* **認証 —**`Digest`

* **ヘッダー —**`Content-Type: text/xml`

* **Body -** XMLを次の例のように指定します。

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

Body内のブ `RepackageList` ロックには、1 ～ 300個のブロックを含めることがで `Repackage` きます。 Body内のブロック数 `Repackage` が300を超える場合、HTTP要求は次のエラーで失敗します。

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


ブロック内の必須および任意選択のパラメ `Repackage` ータは次のとおりです。

* **`AdSystem`** （必須） — ソース広告サーバー( `Auditude`、な `FreeWheel`ど) `Apad.tv`。 VAST要素に対応するstring値です `AdSystem`。

* **`AdId`** （必須） — リクエストで指定されたサードパーティ広告サーバーの識別子です。 VAST応答内の要 `id` 素の属 `Ad` 性に対応します。

* **`CreativeURL`** （必須） — トランスコードする広告クリエイティブの場所(URI)。 これはVAST要素に対応し `MediaFile` ます。

* `CreativeID` （オプション） — 広告エクスペリエンスの一部として含める広告クリエイティブの識別子。
* **`Zone`** （必須） — アカウントのゾーンID（テクニカルアカウントマネージャーから入手）。 これは、Auditudeプラットフォーム設定に対応する数値 `publisher_site_id` です。

* **`Format`** （オプション） — CRSが広告クリエイティブをトランスコードする方法を制御するパラメータ。

   * `clientside` - TVSDKがCDNとの通信に使用するURLと互換性のある出力を生成します。
   >[!IMPORTANT]
   >
   >再パッケージ化された広告をクライアント側の広告挿入と互換性があるようにする場合は、このパラメーターを指定する必要があります。 これを指定しない場合、再パッケージ化された広告は、サーバー側の広告挿入とのみ互換性があります。

   * `hls` - HLS互換のトランスコード広告クリエイティブを生成します。
   * `dash` - DASH互換のトランスコード広告クリエイティブを生成します。
   * `id3` - ID3時間指定メタデータタグをトランスコードされた広告クリエイティブに挿入します。
   * `targetdur`  — トランスコードされた広告クリエイティブのセグメントの時間（秒）。 初期設定はで `targetdur=4`す。 この値は、ターゲット期間タグでマニフェストに指定された値に `<s>` 対応する必要があります。 `#EXT-X-TARGETDURATION:<s>`.
   >[!NOTE]
   >
   >DASH互換のアセットは、Adobe Primetimeの広告挿入と互換性がありません。

>[!IMPORTANT]
>
>再生を最もスムーズにするには、コンテンツ `targetdur` チャンクの長さに合わせてを設定します。

## HTTP応答 {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRSは、次のいずれかのステータスコードでリクエストに応答します。

* **HTTP 202** — 受け入れ済み（空の本文付き）。 これは成功を示します。 CRSは、トランスコードされた広告をCDNサーバにアップロードします。
* **HTTP 400** — 要求が正しくありません。 ポストされたXMLが無効です。
* **HTTP 500** — 内部サーバーエラー。 サーバーで内部の問題が発生しました（例えば、サーバーがデータベースに接続できなかった）。

## SSAIまたはCSAI用のアセットの事前トランスコード {#section_098888BB74FD4DC1AD0BD507B2A48318}

再パッケージ化APIを使用して、今後のSSAIまたはCSAIイベントを事前にトランスコードできます。 アセットが将来SSAIで使用される予定の場合は、POST呼び出しのすべてのパラメーターが一意であることを確認します。 パラメータは次のとおりです。AdSystem、AdId、CreativeURL、Zone、Format。 このパラメータのセットに違いがある場合は、SSAIに対する新しいトランスコードリクエストが発生します。

CSAIで使用されるアセットが将来、アセットの一意性はZoneとCreativeURLに依存します。 AdSystemとAdIdでは、トランスコードされたアセットが異なるわけではなく、クライアントが使用できます。
