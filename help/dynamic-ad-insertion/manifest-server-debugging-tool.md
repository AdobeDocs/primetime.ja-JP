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
source-git-commit: b77f4988103b68d0ce8926407d2ccb2e0c68e322

---


# マニフェストサーバーデバッグツール {#manifest-server-debugging-tool}

## デバッグツールの概要 {#overview-of-debugging-tool}

デバッグツールを使用すると、発行者は、HTTPヘッダーでマニフェストサーバーからリアルタイムに返されたデバッグ情報を調べたり、より詳細な情報が必要な場合に、その後のセッションログを調べたりして、コストのかかる広告挿入の問題を調査できます。 Akamaiなどのアドビのパートナーは、このツールを使用して、Primetime ad decisioningとの統合をデバッグできます。

このツールは、主要なマニフェストサーバー広告トラッキング設定での広告挿入の問題のデバッグをサポートします。

* TVSDKに基づくプレイヤーを使用したクライアント側のトラッキング。
* TVSDKに基づいていないプレーヤーを使用したクライアント側のトラッキング。
* サーバー側の追跡。

これらのすべてのケースをサポートするために、ツールはプレイヤーの発行者コードを必要とせず、使用することもできません。

マニフェストサーバーセッションを開始する際に、リクエストURLにパラメーターを設定し、デバッグ情報のログを取得するようにリクエストURLに指定できます。 このパラメーターの異なる値を使用すると、マニフェストサーバーに指定したデバッグ情報をHTTPヘッダーで返すよう求めることもできますが、ヘッダーに含める情報の量は限られます。 アドビから資格情報を取得して、完全なログファイルにアクセスできます。マニフェストサーバーは、定期的に（例えば、1時間ごとに）アーカイブサーバーに保存します。 そのサーバーの資格情報を取得したら、いつでも直接アクセスできます。

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## デバッグツールのオプション {#debugging-tool-options}

デバッグツールを呼び出すとき、マニフェストサーバーがHTTPヘッダーで返す情報に関して、いくつかのオプションがあります。 このオプションは、マニフェストサーバーがログファイルに配置する内容に影響を与えません。

### ptdebugの指定 {#specifying-ptdebug}

マニフェストサーバーセッションのデバッグログを開始する際に、ptdebugパラメーターを要求URLに追加して、マニフェストサーバーがHTTPヘッダーで返す情報に関する次のオプションを指定できます。

* ptdebug=trueレコードを除き、レコードの `TRACE_HTTP_HEADER` 大部分を `call/response data` 除くすべてのレ `TRACE_AD_CALL` コード。
* ptdebug=AdCall TRACE_AD_*type* （TRACE_AD_CALLなど）レコードのみ。
* ptdebug=Header Only TRACE_HTTP_HEADERレコード。

このオプションは、マニフェストサーバーがログファイルに配置する内容に影響を与えません。 ログファイルはテキストファイルなので、様々なツールを適用して、興味のある情報を抽出し、形式を変更できます。

次に、 `ptdebug=Header`明確にするために、16進数の長い文字列の一部がに置き換 `. . .` えられます。

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

## ログレコードの形式 {#formats-of-log-records}

各ログレコードには、タイプとフィールドのセットがあり、その一部はオプションのものです。 レコードの種類までのすべてのレコードのフィールドは同じです。 タイムスタンプとセッションに関する情報を提供します。 レコードタイプはログに記録されるイベントの種類を識別し、その後のフィールドはログに記録されるイベントに関する情報を提供します。

ログレコードの構造は次のとおりです。

`datetime request_id session_id zone_id record_type` その他のフ *ィールド。*

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| datetime | string | タイムスタンプ |
| request_id | string | マニフェストサーバーで使用される要求ID（UNIXタイムスタンプ） |
| session_id | string | マニフェストサーバーで使用されるセッションID |
| zone_id | 整数 | ゾーンID |
| record_type | string | ログに記録されるイベントのタイプ |
| その他のフィールド | *** | イベントのタイプによる |

### TRACE_REQUEST_INFOレコード {#trace-request-info-records}

このタイプのレコードは、HTTP要求の結果をログに記録します。 TRACE_REQUEST_INFOを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコードを返しました |
| request_method | string | HTTPメソッド（GETまたはPOST） |
| request_uri | string | HTTPリクエストURI（ホストなし） |
| request_length | 整数 | 要求の長さ（バイト） |
| response_length | 整数 | 応答の長さ（バイト） |
| デルタ | 整数 | リクエストの処理に要する時間（ミリ秒） |
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

### TRACE_HTTP_HEADERレコード {#trace-http-header-records}

マニフェストサーバーとクライアント、広告サーバーまたはコンテンツサーバーとの間でHTTP呼び出し中に交換された、このタイプのログHTTPヘッダーのレコード。 TRACE_HTTP_HEADERを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| request_type | string | リクエストのタイプ（メインまたは不明） |
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

### TRACE_AD_CALLレコード {#trace-ad-call-records}

このタイプのレコードは、マニフェストサーバーとリクエストの結果をログに記録します。 TRACE_AD_CALLを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコードを返しました |
| request_duration | 整数 | 要求から応答までの時間（ミリ秒） |
| ad_server_query_url | string | クエリパラメーターを含む、広告呼び出しのURL |
| ad_system_id | string | 広告システム、広告サーバーの応答から（指定されていない場合はAuditude） |
| avail_id | string | コンテンツマニフェストファイル内の広告キューからの値のID（VODの場合は該当なし） |
| avail_duration | number | コンテンツマニフェストファイル内の広告キューからの利用時間（秒）（VODの場合は該当なし） |
| ad_server_response | string | 広告サーバーからのBase64エンコードされた応答 |

例：

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT、TRACE_AD_RESOLVE、およびTRACE_AD_REDIRECTレコード {#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

このタイプのレコードは、レコードタイプで示される広告リクエストの結果をログに記録します。 レコードタイプを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコードを返しました |
| avail_id | string | コンテンツマニフェストファイル（ライブ）内の広告キューまたはマニフェストサーバー(VOD)からの値のID |
| ad_type | string | 広告のタイプ（DIRECTまたはREDIRECT） |
| ad_duration | 整数 | 広告サーバーの応答からの広告の時間（秒） |
| ad_content_url | string | 広告サーバーの応答からの広告のマニフェストファイルのURL |
| ad_content_url_actual | string | 挿入された広告のマニフェストファイルのURL。 TRACE_AD_REDIRECTの場合は空です。 |
| ad_system_id | string | 広告システム、広告サーバーの応答から（指定されていない場合はAuditude） |
| ad_id | string | 広告サーバーの応答からの広告のID |
| creative_id | string | 広告ノードからの、広告サーバーの応答からのクリエイティブのID |
| ad_call_id | string | 使用されません。 将来の使用のために予約。 |
| デルタ | 整数 | このイベントにかかった時間（ミリ秒） |
| misc | string | 理由広告がスキップされました |

>[!NOTE]
>
>ad_content_url_actual、ad_call_idおよびmiscフィールドはオプションです。

TRACE_AD_RESOLVEとTRACE_AD_INSERTの場合、ad_content_url_actualフィールドのURLは、トランスコードされた広告がある場合はその広告のURLです。 それ以外の場合、TRACE_AD_RESOLVEの場合は空、TRACE_AD_INSERTの場合はad_content_urlと同じフィールドです。

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

### TRACE_TRACKING_URLレコード {#trace-tracking-url-records}

このタイプのレコードは、マニフェストサーバーとリクエストの結果をログに記録します。 TRACE_TRACKING_URLを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ポイント | number | プログラムのタイムスタンプ。 URLを呼び出すビデオ内の時間。 |
| ad_system | string | 広告システム（auditudeまたはfreewheel） |
| url | string | URLのpinged |
| 状態 | string | pingから返されたHTTPステータス |

例：

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODEレコード {#trace-transcoding-no-media-to-transcode-records}

このタイプのレコードは、見つからない広告クリエイティブをログに記録します。 TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODEの後の唯一のフィールドがテーブルに表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ad_id | string | 完全修飾広告ID `(FQ_AD_ID: Q_AD_ID[;Q_AD_ID[;Q_AD_ID...]`] Q_AD_ID: `PROTOCOL:AD_SYSTEM:AD_ID[:CREATIVE_ID[:MEDIA_ID]`]プロトコル：AUDITUDE,VAST) |

### TRACE_TRANSCODING_REQUESTEDレコード {#trace-transcoding-requested-records}

このタイプのレコードは、マニフェストサーバーがCRSに送信するトランスコード要求の結果をログに記録します。 TRACE_TRANSCODING_REQUESTEDを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ad_id | string | 完全修飾広告ID |
| ad_manifest_url | string | 広告サーバーの応答からの広告のマニフェストファイルのURL |
| creative_type | string | メディアの種類 |
| フラグ | string | ID3は、トランスコードリクエストにID3タグの追加リクエストが含まれているかどうかを示します |
| target_duration | string | トランスコードされたクリエイティブのターゲット時間（秒） |

### TRACE_TRACKING_REQUESTレコード {#trace-tracking-request-records}

このタイプのレコードは、サーバー側の追跡を行う要求を示します。 TRACE_TRACKING_REQUESTを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| tracking_url_count | 整数 | 追跡URLの数 |
| start | float | PTSフラグメントの開始時間（ミリ秒の精度の秒） |
| end | float | PTSフラグメントの終了時間（ミリ秒の精度の秒） |

### TRACE_TRACKING_REQUEST_URLレコード {#trace-tracking-request-url-records}

このタイプのレコードは、サーバー側の追跡の追跡URLを提供します。 TRACE_TRACKING_REQUEST_URLを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| timestamp | float | 追跡URLにpingを送信する再生セッション内の時間（秒、精度0.001） |
| ad_system | string | 広告システム（例：auditude） |
| url | string | pingを実行するURL |

### TRACE_WEBVTT_REQUESTレコード {#trace-webvtt-request-records}

このタイプのログのレコードは、マニフェストサーバーがWEBVTTキャプションに対して行う要求を行います。 TRACE_WEBVTT_REQUESTを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコードを返しました |
| vtt_uri | string | リクエストのURL |
| start | float | 分割開始時間（秒、ミリ秒精度） |
| end | float | 分割終了時間（秒、ミリ秒の精度） |

### TRACE_WEBVTT_RESPONSEレコード {#trace-webvtt-response-records}

このログ ``of ``をサー ``type ``バー ``responses ``のキャプシ ``manifest ``ョンのキ ``sends ``ャプシ ``clients ```` `answer` ````requests ```for```WEBVTT ``ョンに記録します。 TRACE_WEBVTT_RESPONSEを超えるフィールドは、表に示されるタブで区切られた順序で表示され `by`ます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコードを返しました |
| 応答 | string | クライアントに送信されたBase64エンコードされた応答 |

### TRACE_WEBVTT_SOURCEレコード {#trace-webvtt-source-records}

マニフェストサーバーがWEBVTTキャプションに対して行う要求に対する、このタイプのログ応答のレコードです。 TRACE_WEBVTT_SOURCEを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコードを返しました |
| source | string | Base64エンコードされた元のVTTコンテンツ |


### TRACE_MISCレコード {#trace-misc-records}

このタイプのレコードを使用すると、マニフェストサーバーは、広告を取り込む際に、他に計画されていないイベントや情報をログに記録できます。 TRACE_MISCの後のフィールドは、メッセージ文字列で構成されます。 表示されるメッセージには、次のものがあります。

* 無視された広告：AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*seconds*, ignore=*ignore* redirectRedirectAd=***redirectRedirectAdPriority, priority=ad priority*
* 広告の配置がNULLを返しました。
* 広告が正常に繋ぎ合わされました。
* 広告の呼び出しに失敗しました：エラー *メッセージ*。
* 生のマニフェストを取得するためのUser-Agentの追加： *user-agent*。
* 生のマニフェストを取得するcookieの追加： [cookie]
* URL要求URLが正し *くありません。エラーメッセージ*。 （バリアントURLの解析に失敗しました）
* 呼び出されたURL:URLが返 *されました：応答コード*。 （ライブURL）
* 呼び出されたURL:URLリタ *ーンコード：応答コード*。 (VOD URL)
* 広告の解決中に競合が見つかりました：ミッドロール開始またはミッドロール終了のいずれかが、ミッドロール(VOD)に含まれるプリロールまたはプリロール内にあります。
* URIのハンドラーによって発生した未処理の例外を検出しました：リクエ *ストURL*。
* バリアントマニフェストの生成が完了しました。 （バリアント）
* バリアントマニフェストの生成が完了しました。
* VASTリダイレクトの処理中に例外が発生しました*リダイレクトURL *エラー：エラー *メッセージ*。
* 広告マニフェストURLの広告のプレイリストを取 *得できませんでした*。
* ターゲットマニフェストを生成できませんでした。 (HLSManifestResolver)
* 最初の広告呼び出しの応答を解析できませんでした：エラー *メッセージ*。
* パスに対する*GET|POST *リクエストの処理に失敗しました：リクエ *ストURL*。 （ライブ/VOD）
* ライブマニフェストの要求を処理できませんでした：リクエ *ストURL*。 （ライブ）
* バリアントマニフェストを返せませんでした：エラー *メッセージ*。
* グループIDの検証に失敗しました：グル *ープID*。
* 生のマニフェストの取得：コンテ *ンツのURL*。 （ライブ）
* VASTリダイレクトの後：リダイレ *クトURL*。
* 空白が見つかりました。 (VOD)
* *number *adsが見つかりました。 (VOD)
* HTTP要求を受信しました。 （最初のメッセージ）
* 広告の応答時間(*ad response duration *sec)と実際の広告時間(*actual duration *sec)の差が制限を超えているので、広告は無視されます。 (HLSManifestResolver)
* ID値が指定されなかった値を無視します。 (GroupAdResolver.java)
* 無効な時間値を指定した値を無視します：*time *for availId = *avail ID*.
* 無効な期間の値を指定した値を無視します：*duration *for availId = *avail ID*.
* 新しいセッションを初期化します。 （バリアント）
* HTTPメソッドが無効です。 GETである必要があります。 (VOD)
* HTTPメソッドが無効です。 追跡リクエストはGETである必要があります。 （ライブ）
* 無効なURLが要求さ *れたURLのエラーメッセージ*。 （バリアント）
* 無効なグループです。 (HLSManifestResolver)
* 無効なリクエストです。 キャプションは有効な追跡リクエストではありません。 (VOD)
* 無効なリクエストです。 キャプションの要求は、セッションの確立後に行う必要があります。 (VOD)
* 無効なリクエストです。 トラッキングリクエストは、セッションの確立後に行う必要があります。 (VOD)
* オーバーロードグループIDに対する無効なサーバーインスタンス：グル *ープID*。 （ライブ）
* VASTリダイレクトの制限に達しまし *た —*&#x200B;数。
* 広告の呼び出し：広告 *呼び出しURL*。
* 次のマニフェストが見つかりません：コンテ *ンツのURL*。 （ライブ）
* 有効なIDに一致する値が見つかりません：使用 *可能なID*。 (HLSManifestResolver)
* 再生セッションが見つかりません。 (HLSManifestResolver)
* マニフェストコンテンツURLのVOD *リクエストを処理*。
* バリアントを処理中。
* マニフェストコンテンツURLのキャプショ *ンリクエストを処理*&#x200B;中。
* トラッキングリクエストを処理しています。 (VOD)
* リダイレクト広告の応答が空です。 (VASTStAX)
* リクエスト： *URL*。
* 再生セッションが見つからなかったため、GET要求に対するエラー応答を返しています。 (VOD)
* 内部サーバーエラーが原因で、GET要求に対するエラー応答を返します。
* 無効なアセットを指定したGET要求のエラー応答を返しています：広告 *リクエストID*。 (VOD)
* 無効または空のグループIDを指定したGET要求のエラー応答を返します：グル *ープID*。 (VOD)
* 無効な追跡位置の値を指定したGETリクエストのエラー応答を返します。 (VOD)
* 構文が無効なGET要求に対するエラー応答を返します — 要 *求URL*。 （ライブ/VOD）
* サポートされていないHTTPメソッドを使用した要求に対するエラー応答を返します： *GET|POST*. （ライブ/VOD）
* キャッシュからマニフェストを返しています。 (VOD)
* サーバーが過負荷です。 広告ステッチのリクエストなしで続行します。 （バリアント）
* ターゲットマニフェストの生成を開始します。 (HLSManifestResolver)
* バリアントマニフェストの生成の開始：コンテ *ンツのURL*。 （バリアント）
* 広告のマニフェストへのステッチを開始します。 (VODHLSResolver)
* HH:MM:SSで広告をス *テッチしようとしています*:AdPlacementManifestURL=*Manifest URL*, durationSeconds=*seconds*, ignore=*redirectRedirectRedirectAd**ignore*, priority=*priority priority* Manifest (HLSManifestResolver)
* pttimelineが無効なため、広告を取得できません — 広告なしでコンテンツを返しました。 (VOD)
* 広告を取得できません — 広告なしでコンテンツを返しました。 (VOD)
* 広告クエリを取得できず、コンテンツURLが指定されていません。 (VOD)
* 受け取った有効なURL。 （VOD/バリアント）
* バリアントM3U8が見つかりません。 （バリアント）

### TRACE_TRACKING_URLレコード {#trace-tracking-url-records-1}

マニフェストサーバは、サーバ側トラッキングワークフロー中にトラッキングURLを呼び出した後、この種のレコードを生成する。 TRACE_TRACKING_URLを超えるフィールドは、表に示す順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| ポイント | number | ストリーム内のPTS時間 |
| ad_system | string | 広告の広告システム（auditudeまたはfreewheel） |
| url | string | URLのpinged |
| state | string | HTTPステータスコード |

### TRACE_PLAYBACK_PROGRESSレコード {#trace-playback-progress-records}

マニフェストサーバーは、サーバー側の追跡ワークフロー中に再生の進行状況に関する信号を受け取ると、この種のレコードを生成します。 TRACE_PLAYBACK_PROGRESSを超えるフィールドは、表に示されている順序で、タブで区切って表示されます。

| フィールド | タイプ | 説明 |
|--- |--- |--- |
| 状態 | string | HTTPステータスコード |
| 帯域幅 | 整数 | ストリームの帯域幅 |
| ポイント | 整数 | ストリーム内のPTS時間 |
| ms_time | 整数 | マニフェストサーバーが追跡URLを生成した時間 |
| url | string | リダイレクトURL |
| header_user_agent | string | HTTP User-Agentヘッダー |
| header_dnt | 整数 | HTTP do-not-trackヘッダ |
| effective_remote_address | string | IPv4有効リモートアドレス |
| remote_address | string | IPv4リモートアドレス |

>[!NOTE]
>
>最後の4つのフィールドはオプションです。

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。
