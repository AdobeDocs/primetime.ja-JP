---
title: マニフェストサーバーデバッグツール
seo-title: マニフェストサーバーデバッグツール
description: マニフェストサーバーデバッグツール
seo-description: マニフェストサーバーデバッグツール
uuid: 0b4f06f5-4b1f-4f88-980a-5b4df28e0094
products: SG_PRIMETIME
topic-tags: ad-insertion
discoiquuid: 00b49659-ce56-4b5c-87cd-c357a0936641
donotlocalize: false
moreHelpPaths: /content/help/en/primetime/morehelp/ad-insertion;/content/help/en/primetime/morehelp/ad-insertion
pagecreatedat: en
pagelayout: video
sidecolumn: left
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '2422'
ht-degree: 0%

---


# マニフェストサーバーデバッグツール{#manifest-server-debugging-tool}

デバッグツールを使用すると、発行者は、HTTPヘッダーでマニフェストサーバーからリアルタイムに返されるデバッグ情報を調べたり、より詳細な情報が必要な場合は、その後セッションログを調べたりして、コストのかかる広告挿入の問題を調査できます。 AkamaiなどのAdobeパートナーは、このツールを使用して、Primetime ad decisioningとの統合をデバッグできます。

このツールは、主要なマニフェストサーバー広告トラッキング設定での広告挿入の問題のデバッグをサポートします。

* TVSDKに基づくプレイヤーを使用したクライアント側トラッキング。
* TVSDKに基づいていないプレイヤーを使用したクライアント側のトラッキング。
* サーバー側のトラッキング。

これらのすべてのケースをサポートするために、ツールはプレイヤーの発行者コードを必要としないか、使用しません。

マニフェストサーバーセッションを開始すると、リクエストURLにパラメーターを設定して、デバッグ情報のログを求めることができます。 このパラメーターの異なる値を使用すると、マニフェストサーバーに指定したデバッグ情報をHTTPヘッダーで返すよう求めることもできますが、ヘッダーに含める情報の量は限られます。 Adobeから秘密鍵証明書を取得して完全なログファイルにアクセスできます。このログファイルは、マニフェストサーバーが定期的にアーカイブサーバーに保存（1時間ごとなど）されます。 そのサーバーの資格情報を取得すると、いつでも直接アクセスできます。

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## デバッグツールのオプション{#debugging-tool-options}

デバッグツールを呼び出すとき、マニフェストサーバーがHTTPヘッダーで返す情報に関して、いくつかのオプションがあります。 このオプションは、マニフェストサーバーがログファイルに配置する内容には影響しません。

### ptdebug {#specifying-ptdebug}の指定

マニフェストサーバーセッションのデバッグログを開始する場合、ptdebugパラメーターを要求URLに追加して、マニフェストサーバーがHTTPヘッダーで返す情報に関する次のオプションを指定できます。

* ptdebug=true `TRACE_HTTP_HEADER`レコードと`TRACE_AD_CALL`レコードのほとんどの`call/response data`を除くすべてのレコード。
* ptdebug=AdCallTRACE_AD_*タイプ*(例えば、TRACE_AD_CALL)レコードのみ。
* ptdebug=HeaderのみのTRACE_HTTP_HEADERレコード

このオプションは、マニフェストサーバーがログファイルに配置する内容には影響しません。 ログファイルはテキストファイルです。このため、様々なツールを適用して、関心のある情報を抽出し、形式を変更できます。

`ptdebug=Header`の際に返されるHTTPヘッダの例を以下に示します。 16進数の長い文字列の一部は、明確にするために`. . .`に置き換えられます。

```
X-ADBE-AI-DBG-1 TRACE_MISC    HTTP request received
X-ADBE-AI-DBG-2 TRACE_MISC    Processing Variant
X-ADBE-AI-DBG-3 TRACE_MISC    Valid URL received.
X-ADBE-AI-DBG-4 TRACE_MISC    Initialize new session
X-ADBE-AI-DBG-5 TRACE_MISC    Requesting: /auditude/variant/pubAsset/aHR0cDovL . . .m3u8
 ?u=cecebae . . .&z=189962&pttrackingmode=simple&pttrackingversion=v1
 &ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true
X-ADBE-AI-DBG-6  TRACE_HTTP_HEADER  MAIN  REQUEST  Host    bWFuaWZl. . .
X-ADBE-AI-DBG-7  TRACE_HTTP_HEADER  MAIN  REQUEST  Connection       Y2xvc2U=
X-ADBE-AI-DBG-8  TRACE_HTTP_HEADER  MAIN  REQUEST  Accept   dGV4dC. . .
X-ADBE-AI-DBG-9  TRACE_HTTP_HEADER  MAIN  REQUEST  Cookie   c3NhaT. . .
X-ADBE-AI-DBG-10 TRACE_HTTP_HEADER  MAIN  REQUEST  User-Agent       TW96aWxs. . .
X-ADBE-AI-DBG-11 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Language  ZW4tdXM=
X-ADBE-AI-DBG-12 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Encoding  Z3ppcCwg. . .=
X-ADBE-AI-DBG-13 TRACE_REQUEST_INFO  200   GET
 /auditude/variant/pubAsset/aHR0cD. . ..m3u8
 ?u=cecebae72a919de350b9ac52602623f3&z=189962&pttrackingmode=simple
 &pttrackingversion=v1&ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true   0 0 0   Variant  NA  null  null  127.0.0.1:43357
X-ADBE-AI-DBG-14 TRACE_HTTP_HEADER  MAIN  RESPONSE Content-Type     YXBwbG. . .
X-ADBE-AI-DBG-15 TRACE_HTTP_HEADER  MAIN  RESPONSE Cache-Control    bm8tY2. . .
X-ADBE-AI-DBG-16 TRACE_HTTP_HEADER  MAIN  RESPONSE Access-Control-Allow-Origin    Kg==
X-ADBE-AI-DBG-17 TRACE_MISC   Done
```

## ログレコードの形式{#formats-of-log-records}

各ログレコードにはタイプとフィールドのセットがあり、その一部はオプションです。 レコードの種類に対応するすべてのレコードのフィールドは同じです。 タイムスタンプとセッションに関する情報を提供します。 レコードタイプはログに記録されるイベントの種類を識別し、後続のフィールドはログに記録されるイベントに関する情報を提供します。

ログレコードの構造は次のとおりです。

`datetime request_id session_id zone_id record_type` *その他のフィールド。*

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| datetime | string | Timestamp |
| request_id | string | マニフェストサーバーで使用されるリクエストID（UNIXタイムスタンプ） |
| session_id | string | マニフェストサーバーで使用されるセッションID |
| zone_id | integer | ゾーンID |
| record_type | string | ログに記録されるイベントの種類 |
| その他のフィールド | *** | イベントの種類に応じて異なる |

### TRACE_要求_INFOレコード{#trace-request-info-records}

このタイプのレコードは、HTTP要求の結果を記録します。 TRACE_REQUEST_INFOより後のフィールドは、表に示す順序で表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | 返されたHTTPステータスコード |
| request_method | string | HTTPメソッド(GETまたはPOST) |
| request_uri | string | HTTP要求URI （ホストなし） |
| request_length | integer | 要求の長さ（バイト） |
| response_length | integer | 応答の長さ（バイト） |
| delta | integer | 要求を処理する時間（ミリ秒） |
| module_type | string | バリアント、ストリームまたはVOD |
| remote_address_aud_client_ip | string | （注を参照）。 |
| remote_address_x_fwd_for_hdr_key | string | （注を参照）。 |
| remote_host_port | string | （注を参照）。 |

>[!NOTE]
>
>最後の3つのフィールドはオプションです。

例：

```
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938
TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8
?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADERレコード{#trace-http-header-records}

マニフェストサーバーとクライアント、広告サーバー、またはコンテンツサーバーとの間でHTTP呼び出し中に交換された、このタイプのログHTTPヘッダーのレコードです。 TRACE_HTTP_HEADERより後のフィールドは、表に示す順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| request_type | string | 要求のタイプ（MAINまたはUNKNOWN） |
| request_response | string | 応答ヘッダー（リクエストまたは応答） |
| header_name | string | HTTPヘッダー名 |
| header_value | string | Base64エンコードされたHTTPヘッダー値 |

>[!NOTE]
>
>request_typeフィールドとheader_valueフィールドはオプションです。

例：

```
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_MISC
    Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST Cookie  aGRu. . .
2015-03-25T06:10:00.928Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST User-Agent  TW96aW. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Server  bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Content-Type    YXBwb. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Last-Modified   V2VkL. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  ETag    IjIyY2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Vary    QWNjZXB. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Cache-Control   bWF4LW. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Expires V2VkL. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Date    V2VkLCA. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Age MQ==
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Via MS4xIH. . .
```

### TRACE_AD_CALLレコード{#trace-ad-call-records}

このタイプのレコードは、マニフェストサーバー広告リクエストの結果をログに記録します。 TRACE_AD_CALLより後のフィールドは、表に示す順序で表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | 返されたHTTPステータスコード |
| request_duration | integer | 要求から応答までの時間（ミリ秒） |
| ad_server_クエリ_url | string | 広告呼び出しのURL(クエリパラメーターを含む) |
| ad_system_id | string | 広告サーバーの応答からの広告システム（指定しない場合はAuditude） |
| avail_id | string | コンテンツマニフェストファイル内の広告キューからの利用者のID（VODの場合は該当なし） |
| avail_duration | number | コンテンツマニフェストファイル内の広告キューからの有効時間（秒）（VODの場合は該当なし） |
| ad_server_response | string | 広告サーバーからのBase64エンコードされた応答 |

例：

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT、TRACE_AD_RESOLVE、TRACE_AD_REDIRECTレコード{#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

このタイプのレコードは、レコードタイプで示される広告リクエストの結果を記録します。 レコードの種類を超えたフィールドは、表に示されている順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | 返されたHTTPステータスコード |
| avail_id | string | コンテンツマニフェストファイル（ライブ）内の広告キューまたはマニフェストサーバー(VOD)からの利用可能なID |
| ad_type | string | 広告のタイプ（DIRECTまたはREDIRECT） |
| ad_duration | integer | 広告サーバーの応答からの広告の時間（秒） |
| ad_content_url | string | 広告サーバーのレスポンスからの広告のマニフェストファイルのURL |
| ad_content_url_actual | string | 挿入された広告のマニフェストファイルのURL。 TRACE_AD_REDIRECTの場合は空です。 |
| ad_system_id | string | 広告サーバーの応答からの広告システム（指定しない場合はAuditude） |
| ad_id | string | 広告サーバーの応答からの広告のID |
| creative_id | string | 広告ノードからの広告サーバーの応答からのクリエイティブのID |
| ad_call_id | string | 未使用。 将来的に使用するために予約されています。 |
| delta | integer | このイベントにかかった時間（ミリ秒） |
| misc | string | 理由広告がスキップされました |

>[!NOTE]
>
>ad_content_url_actual、ad_call_idおよびmiscフィールドはオプションです。

TRACE_AD_RESOLVEとTRACE_AD_INSERTの場合、ad_content_url_actualフィールドのURLは、トランスコードされた広告（存在する場合）に使用されます。 それ以外の場合は、TRACE_AD_RESOLVEの場合は空、TRACE_AD_INSERTの場合はad_content_urlと同じフィールドです。

例：

```
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

### TRACE_TRACKING_URLレコード{#trace-tracking-url-records}

このタイプのレコードは、マニフェストサーバー広告リクエストの結果をログに記録します。 TRACE_TRACKING_URLより後のフィールドは、表に示す順序で、タブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ポイント | number | プログラムのタイムスタンプ。 URLを呼び出すビデオ内の時間。 |
| ad_system | string | 広告システム（auditudeまたはfreewheel） |
| url | string | URLのピング |
| status | string | pingから返されたHTTPステータス |

例：

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODEレコード{#trace-transcoding-no-media-to-transcode-records}

このタイプのレコードは、見つからない広告クリエイティブをログに記録します。 TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODEの後の唯一のフィールドが表に表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ad_id | string | 完全修飾広告ID `(FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\]\]` Q_AD_ID:`PROTOCOL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\]\]`プロトコル：AUDITUDE,VAST) |

### TRACE_TRANSCODING_REQUESTEDレコード{#trace-transcoding-requested-records}

このタイプのレコードは、マニフェストサーバーがCRSに送信するトランスコード要求の結果を記録します。 TRACE_TRANSCODING_REQUESTEDの後のフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ad_id | string | 完全修飾広告ID |
| ad_manifest_url | string | 広告サーバーのレスポンスからの広告のマニフェストファイルのURL |
| creative_type | string | メディアの種類 |
| flags | string | ID3は、トランスコードリクエストにID3タグの追加のリクエストが含まれているかどうかを示します |
| ターゲット期間 | string | トランスコードされたクリエイティブのターゲット時間（秒） |

### TRACE_TRACKING_REQUESTレコード{#trace-tracking-request-records}

このタイプのレコードは、サーバー側の追跡を行うリクエストを示します。 TRACE_TRACKING_REQUESTより後のフィールドは、表に示す順序で、タブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| tracking_url_count | integer | 追跡URLの数 |
| 開始 | float | PTSフラグメント開始時間（ミリ秒精度の秒） |
| end | float | PTSフラグメントの終了時間（ミリ秒の精度の秒） |

### TRACE_TRACKING_REQUEST_URLレコード{#trace-tracking-request-url-records}

このタイプのレコードは、サーバー側の追跡の追跡URLを提供します。 TRACE_TRACKING_REQUEST_URLより後のフィールドは、表に示された順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| timestamp | float | 再生セッション内で追跡URLにpingを実行する時間（秒、精度0.001） |
| ad_system | string | 広告システム（auditudeなど） |
| url | string | URL to ping |

### TRACE_WEBVTT_REQUESTレコード{#trace-webvtt-request-records}

このタイプのログのレコードは、マニフェストサーバーがWEBVTTキャプションに対して行う要求を行います。 TRACE_WEBVTT_REQUESTより後のフィールドは、表に示されている順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | 返されたHTTPステータスコード |
| vtt_uri | string | リクエストのURL |
| 開始 | float | 分割開始時間（秒、ミリ秒の精度） |
| end | float | 分割終了時間（ミリ秒精度の秒数） |

### TRACE_WEBVTT_RESPONSEレコード{#trace-webvtt-response-records}

``of ``この``type ``ログ``responses ````manifest ``サーバー``sends ``を`` `answer` ``の``clients ``に``requests `` `for` ``WEBVTT ``キャプションに記録します。 TRACE_WEBVTT_RESPONSE &quot;を超えるフィールドは、表に示す順に表示され、`by`タブが区切られて表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | 返されたHTTPステータスコード |
| response | string | クライアントに送信されるBase64エンコードされた応答 |

### TRACE_WEBVTT_SOURCEレコード{#trace-webvtt-source-records}

マニフェストサーバーがWEBVTTキャプションに対して行う要求に対する、このタイプのログ応答のレコードです。 TRACE_WEBVTT_SOURCEより後のフィールドは、表に示されている順序で、タブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | 返されたHTTPステータスコード |
| source | string | Base64エンコードされた元のVTTコンテンツ |


### TRACE_MISCレコード{#trace-misc-records}

このタイプのレコードを使用すると、マニフェストサーバーが広告を取り込む際に、特別に計画されていないイベントと情報をログに記録できます。 TRACE_MISCの後のフィールドは、メッセージ文字列で構成されます。 表示されるメッセージには、次のようなものがあります。

* Adは無視されました：AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirectAd*, priority=**
* 広告の配置がNULLを返しました。
* 広告は正常に繋ぎ合わせられました。
* 広告呼び出しに失敗しました：*エラーメッセージ*。
* 生のマニフェストを取得するためのUser-Agentの追加：*user-agent*.
* 生のマニフェストを取得するためのcookieの追加：[cookie]
* 不正なURL *要求されたURLエラーメッセージ*。 （バリアントURLの解析に失敗しました）
* 呼び出されたURL:URL *が返されました：応答コード*。 （ライブURL）
* 呼び出されたURL:URL *リターンコード：応答コード*。 (VOD URL)
* 広告の解決中に競合が見つかりました：ミッドロール開始またはミッドロールエンドのいずれかが、ミッドロール(VOD)に含まれるプリロールまたはプリロール内にあります。
* URIのハンドラーによって発生した未処理の例外を検出しました：*リクエストURL*。
* バリアントマニフェストの生成が完了しました。 （バリアント）
* バリアントマニフェストの生成が完了しました。
* VASTリダイレクト*リダイレクトURL *エラーの処理中に例外が発生しました：*エラーメッセージ*。
* *広告マニフェストURL*&#x200B;の広告のプレイリストを取得できませんでした。
* 対象のマニフェストを生成できませんでした。 (HLSManifestResolver)
* 最初の広告呼び出しの応答を解析できませんでした：*エラーメッセージ*。
* *GET|POST*パスの要求を処理できませんでした：*リクエストURL*。 （ライブ/VOD）
* ライブマニフェスト要求を処理できませんでした：*リクエストURL*。 （ライブ）
* バリアントマニフェストを返せませんでした：*エラーメッセージ*。
* グループIDの検証に失敗しました：*グループID*。
* 生のマニフェストの取得：*コンテンツURL*。 （ライブ）
* VASTリダイレクトに従う：*リダイレクトURL*。
* 空が見つかりました。 (VOD)
* *number *adsが見つかりました。 (VOD)
* HTTP要求を受信しました。 （最初のメッセージ）
* 広告の応答時間(*ad response duration *sec)と実際の広告時間(*actual duration *sec)の差が制限を超えているので、広告を無視します。 (HLSManifestResolver)
* ID値が指定されなかった値を無視します。 (GroupAdResolver.java)
* 無効な時間値が指定された値を無視します：*time *for availId = *avail ID*.
* 無効な期間値が指定された値を無視します：*duration *for availId = *avail ID*.
* 新しいセッションを初期化します。 （バリアント）
* 無効なHTTPメソッドです。 GETにする必要があります。 (VOD)
* 無効なHTTPメソッドです。 トラッキングリクエストはGETである必要があります。 （ライブ）
* 無効なURL *要求されたURLエラーメッセージ*&#x200B;です。 （バリアント）
* 無効なグループです。 (HLSManifestResolver)
* 無効な要求です。 キャプションは有効な追跡リクエストではありません。 (VOD)
* 無効な要求です。 キャプションの要求は、セッションの確立後に行う必要があります。 (VOD)
* 無効な要求です。 トラッキングリクエストは、セッションの確立後に行う必要があります。 (VOD)
* オーバーロードグループIDに対する無効なサーバーインスタンス：*グループID*。 （ライブ）
* VASTリダイレクトの制限に達しました — *数値*。
* 広告の呼び出し：*広告呼び出しURL*。
* 次のマニフェストが見つかりません：*コンテンツURL*。 （ライブ）
* 有効なIDに一致する値が見つかりません：*利用可能なID*。 (HLSManifestResolver)
* 再生セッションが見つかりません。 (HLSManifestResolver)
* マニフェスト&#x200B;*コンテンツURL*&#x200B;に対するVODリクエストを処理しています。
* バリアントを処理中です。
* マニフェスト&#x200B;*コンテンツURL*&#x200B;のキャプション要求を処理しています。
* トラッキングリクエストを処理しています。 (VOD)
* リダイレクト広告の応答が空です。 (VASTStAX)
* リクエスト：*URL*。
* 再生セッションが見つからなかったため、GETリクエストに対するエラー応答を返します。 (VOD)
* 内部サーバーエラーが原因で、GETリクエストに対するエラー応答を返します。
* 無効なアセットを指定したGET要求に対するエラー応答を返す：*広告リクエストID*。 (VOD)
* 無効または空のグループIDを指定したGET要求に対するエラー応答を返す：*グループID*。 (VOD)
* 無効な追跡位置の値を指定したGETリクエストに対するエラー応答を返します。 (VOD)
* 無効な構文を持つGETリクエストに対するエラー応答を返します — *リクエストURL*。 （ライブ/VOD）
* サポートされていないHTTPメソッドを使用した要求に対するエラー応答を返します：*GET|POST*。 （ライブ/VOD）
* キャッシュからマニフェストを返しています。 (VOD)
* サーバーが過負荷の状態です。 広告ステッチ要求なしで続行します。 （バリアント）
* 対象のマニフェストを生成中に開始が発生しました。 (HLSManifestResolver)
* 次からバリアントマニフェストを生成中に開始が発生しました：*コンテンツURL*。 （バリアント）
* 開始が広告をマニフェストにステッチしています。 (VODHLSResolver)
* `HH:MM:SS`で広告をステッチしようとしています：AdPlacement \[adManifestURL=*広告マニフェストURL*、durationSeconds=*seconds*、ignore=*ignore*、redirectAd=*redirect ad*、priority=*a10/\。]*
* pttimelineが無効なため、広告を取得できません — 広告のないコンテンツを返しました。 (VOD)
* 広告を取得できません — 広告のないコンテンツを返しました。 (VOD)
* 広告のクエリを取得できず、コンテンツURLが指定されませんでした。 (VOD)
* 受け取った有効なURL。 （VOD/バリアント）
* バリアントM3U8が見つかりません。 （バリアント）

### TRACE_TRACKING_URLレコード{#trace-tracking-url-records-1}

マニフェストサーバーは、サーバー側のトラッキングワークフロー中にトラッキングURLを呼び出した後、この種のレコードを生成します。 TRACE_TRACKING_URLより後のフィールドは、表に示す順序で、タブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ポイント | number | ストリーム内のPTS時間 |
| ad_system | string | 広告の広告システム（auditudeまたはfreewheel） |
| url | string | URLのピング |
| state | string | HTTPステータスコード |

### TRACE_PLAYBACK_PROGRESSレコード{#trace-playback-progress-records}

マニフェストサーバーは、サーバー側のトラッキングワークフロー中に再生進行に関するシグナルを受け取ると、この種のレコードを生成します。 TRACE_PLAYBACK_PROGRESSの後のフィールドは、表に示されている順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| status | string | HTTPステータスコード |
| 帯域幅 | integer | ストリームの帯域幅 |
| ポイント | integer | ストリーム内のPTS時間 |
| ms_time | integer | マニフェストサーバーがトラッキングURLを生成した時間 |
| url | string | リダイレクトURL |
| header_user_agent | string | HTTP User-Agentヘッダー |
| header_dnt | integer | HTTP追跡しないヘッダー |
| effective_remote_address | string | IPv4有効リモートアドレス |
| remote_address | string | IPv4リモートアドレス |

>[!NOTE]
>
>最後の4つのフィールドはオプションです。

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。
