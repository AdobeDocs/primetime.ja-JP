---
title: 詳細ログ
description: 詳細ログ
copied-description: true
exl-id: f2d1b0c2-ba28-4fba-9a4e-71d1421f37fe
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '2157'
ht-degree: 0%

---

# 詳細ログ{#verbose-logging}

## ptdebug/loggingイベントの説明{#ptdebug-logging-events}

マニフェストサーバーセッションのデバッグログを開始する際に、`ptdebug`パラメーターを要求URLに追加して、マニフェストサーバーがHTTPヘッダーで返す情報に関する次のオプションを指定できます。

* `ptdebug=true`
TRACE_HTTP_HEADERと、TRACE_AD_CALLレコードからのほとんどの呼び出し/応答データを除くすべてのレコード。

* `ptdebug=AdCall`
TRACE_AD_型(例えば、TRACE_AD_CALL)のレコードのみ。

* `ptdebug=Header`
TRACE_HTTP_HEADERレコードのみ。

## ログレコードの形式{#log-record-formats}

各ログレコードにはタイプとフィールドのセットがあり、その一部はオプションです。 レコードの種類に対応するすべてのレコードのフィールドは同じです。 タイムスタンプとセッションに関する情報を提供します。 レコードタイプはログに記録されるイベントの種類を識別し、後続のフィールドはログに記録されるイベントに関する情報を提供します。

ログレコードの構造は次のとおりです。

`datetime request_id session_id zone_id record_type other fields`.

| フィールド | タイプ | 説明 |
|---|---|---|
| datetime | string | Timestamp |
| request_id | string | マニフェストサーバーで使用される要求ID（UNIXタイムスタンプ） |
| session_id | string | マニフェストサーバーで使用されるセッションID |
| zone_id | integer | ゾーン |
| record_type | string | ログに記録されるイベントの種類 |
| その他のフィールド | 異なる | イベントの種類に応じて異なる |

このタイプのレコードは、HTTP要求の結果を記録します。 `TRACE_REQUEST_INFO`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | 返されたHTTPステータスコード |
| request_method | string | HTTPメソッド(GETまたはPOST) |
| request_uri | string | HTTP要求URI （ホストなし） |
| request_length | integer | 要求の長さ（バイト） |
| response_length | integer | 応答の長さ（バイト） |
| delta | integer | 要求を処理する時間（ミリ秒） |
| module_type | string | バリアント、ストリームまたはVOD |
| remote_address_aud_client_ip | string | **△** |
| remote_address_x_fwd_for_hdr_key | string | **△** |
| remote_host_port | string | **△** |

**△** 最後の3つのフィールドはオプションです。

**例**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADERレコード{#trace-http-header-records}

マニフェストサーバーとクライアント、広告サーバー、またはコンテンツサーバーとの間でHTTP呼び出し中に交換された、このタイプのログHTTPヘッダーのレコードです。 TRACE_HTTP_HEADERより後のフィールドは、表に示す順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| request_type | string | 要求のタイプ（MAINまたはUNKNOWN） |
| request_response | string | 応答ヘッダー（リクエストまたは応答） |
| header_name | string | HTTPヘッダー名 |
| header_value | string | Base64エンコードされたHTTPヘッダー値 |

>[!NOTE]
>
>`request_type`フィールドと`header_value`フィールドはオプションです。

**例**

```shell
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_MISC Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST Cookie aGRu. . .
2015-03-25T06:10:00.928Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST User-Agent TW96aW. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Server bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Content-Type YXBwb. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Last-Modified V2VkL. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE ETag IjIyY2. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Vary QWNjZXB. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Cache-Control bWF4LW. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Expires V2VkL. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Date V2VkLCA. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Age MQ==
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Via MS4xIH. . .
```

### TRACE_AD_CALLレコード{#tracing-ad-call-records}

このタイプのレコードは、マニフェストサーバー広告リクエストの結果をログに記録します。 `TRACE_AD_CALL`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | 返されたHTTPステータスコード |
| request_duration | integer | 要求から応答までの時間（ミリ秒） |
| ad_server_クエリ_url | string | 広告呼び出しのURL(クエリパラメーターを含む) |
| ad_system_id | string | 広告サーバーの応答からの広告システム（指定しない場合はAuditude） |
| avail_id | string | コンテンツマニフェストファイル内の広告キューからの利用者のID（VODの場合は該当なし） |
| avail_duration | number | コンテンツマニフェストファイル内の広告キューからの有効時間（秒）（VODの場合は該当なし） |
| ad_server_response | string | 広告サーバーからのBase64エンコードされた応答 |

例：

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT、TRACE_AD_RESOLVE、TRACE_AD_REDIRECTレコード{#trace-ad-insert-resolve-redirect}

このタイプのレコードは、レコードタイプで示される広告リクエストの結果を記録します。 レコードの種類を超えたフィールドは、表に示されている順序でタブで区切って表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | HTTPステータスコードを返しました。 |
| avail_id | string | コンテンツマニフェストファイル（ライブ）内の広告キューまたはマニフェストサーバー(VOD)から取得した、利用可能なID。 |
| ad_type | string | 広告のタイプ（DIRECTまたはREDIRECT）。 |
| ad_duration | integer | 広告サーバーの応答からの広告の時間（秒）。 |
| ad_content_url | string | 広告サーバーの応答からの広告のマニフェストファイルのURL。 |
| **†** ad_content_url_actual | string | 挿入された広告のマニフェストファイルのURL。 TRACE_AD_REDIRECTの場合は空です。 |
| ad_system_id | string | 広告システム、広告サーバーの応答（指定しない場合はAuditude）から取得。 |
| ad_id | string | 広告サーバーの応答からの広告のID。 |
| creative_id | string | 広告ノードからの広告サーバーの応答からのクリエイティブのID。 |
| **†** ad_call_id | string | 未使用。 将来的に使用するために予約されています。 |
| delta | integer | このイベントにかかった時間（ミリ秒）です。 |
| **†** その他 | string | 理由広告がスキップされました。 |

**** `ad_content_url_actual`†、 `ad_call_id`および `misc` フィールドはオプションです。

>[!NOTE]
>
>`TRACE_AD_RESOLVE`と`TRACE_AD_INSERT`の場合、`ad_content_url_actual`フィールドのURLは、トランスコードされた広告のURLです（利用可能な場合）。 それ以外の場合は、`TRACE_AD_RESOLVE`の場合は空、`TRACE_AD_INSERT`の場合は`ad_content_url`と同じです。

例：

```shell
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

<!-- ### TRACE_TRACKING_URL records {#trace-tracking-url-records}

Records of this type log the results of manifest server ad requests. Fields beyond `TRACE_TRACKING_URL` appear in the order shown in the table, separated by tabs.

| Field | Type | Description |
|---|---|---|
| pts | number | Program timestamp. Time within video to call the URL. |
| ad_system | string | Ad system (auditude or freewheel) |
| url | string | URL pinged |
| status | string | HTTP status returned from the ping |

```shell
2015-06-04T23:24:42.000-0700 1426742736208 3086f5cd . . . 12345 TRACE_TRACKING_URL 0.000000 ExampleSystem https://localhost/index.php?stream:test#8.1433485415; sid:3086f5cd . . .;pts:0 200
```

-->

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODEレコード{#trace-transcoding-no-media-to-transcode}

このタイプのレコードは、見つからない広告クリエイティブをログに記録します。 `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE`の後の唯一のフィールドがテーブルに表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ad_id | string | 完全修飾広告ID(FQ_AD_ID:Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\] \] Q_AD_ID:プロトコル：AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \]プロトコル：AUDITUDE,VAST) |

このタイプのレコードは、マニフェストサーバーがCRSに送信するトランスコード要求の結果を記録します。 `TRACE_TRANSCODING_REQUESTED`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ad_id | string | 完全修飾広告ID |
| ad_manifest_url | string | 広告サーバーのレスポンスからの広告のマニフェストファイルのURL |
| creative_type | string | メディアの種類 |
| flags | string | ID3は、トランスコードリクエストにID3タグの追加のリクエストが含まれているかどうかを示します |
| ターゲット期間 | string | トランスコードされたクリエイティブのターゲット時間（秒） |

このタイプのレコードは、サーバー側の追跡を行うリクエストを示します。 `TRACE_TRACKING_REQUEST`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| tracking_url_count | integer | 追跡URLの数 |
| 開始 | float | PTSフラグメント開始時間（ミリ秒精度の秒） |
| end | float | PTSフラグメントの終了時間（ミリ秒の精度の秒） |

このタイプのレコードは、サーバー側の追跡の追跡URLを提供します。 `TRACE_TRACKING_REQUEST_URL`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| timestamp | float | 再生セッション内の時間（秒、精度0.001）。トラッキングURLにpingを送信します。 |
| ad_system | string | 広告システム（auditudeなど） |
| url | string | URL to ping |

このタイプのログのレコードは、マニフェストサーバーが`WEBVTT`キャプションに対して行う要求です。 `TRACE_WEBVTT_REQUEST`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | 返されたHTTPステータスコード |
| vtt_uri | string | リクエストのURL |
| 開始 | float | 分割開始時間（秒、ミリ秒の精度） |
| end | float | 分割終了時間（ミリ秒精度の秒数） |

このタイプのログ応答のレコードは、マニフェストサーバーが`answer`内のクライアントに送信し、`WEBVTT`キャプションの要求を行います。 `TRACE_WEBVTT_RESPONSE`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | 返されたHTTPステータスコード |
| response | string | クライアントに送信されるBase64エンコードされた応答 |

マニフェストサーバーが`WEBVTT`キャプションに対して行う要求に対する、このタイプのログ応答のレコードです。 `TRACE_WEBVTT_SOURCE`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | 返されたHTTPステータスコード |
| source | string | Base64エンコードされた元のVTTコンテンツ |

このタイプのレコードを使用すると、マニフェストサーバーが広告を取り込む際に、特別に計画されていないイベントと情報をログに記録できます。 `TRACE_MISC`の後のフィールドは、メッセージ文字列で構成されています。 表示されるメッセージには、次のようなものがあります。

* 無視された広告：AdPlacement \[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb....m3u8、durationSeconds=15.0、ignore=false、redirectAd=false、priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= seconds, ignore= ignore, redirectAd= redirectAd, priority= priority
* 広告の配置がNULLを返しました。
* 広告は正常に繋ぎ合わせられました。
* 広告呼び出しに失敗しました：エラーメッセージ。
* 生のマニフェストを取得するためのUser-Agentの追加：user-agent.
* 生のマニフェストを取得するためのcookieの追加：#
* URL要求URLが正しくありません。エラーメッセージが表示されます。 （バリアントURLの解析に失敗しました）
* 呼び出されたURL:URLが戻り値：応答コード。 （ライブURL）
* 呼び出されたURL:URLリターンコード：応答コード。 (VOD URL)
* 広告の解決中に競合が見つかりました：ミッドロール開始またはミッドロールエンドのいずれかが、ミッドロール(VOD)に含まれるプリロールまたはプリロール内にあります。
* URIのハンドラーによって発生した未処理の例外を検出しました：リクエストURL
* バリアントマニフェストの生成が完了しました。 （バリアント）
* バリアントマニフェストの生成が完了しました。
* VASTリダイレクト*リダイレクトURL *エラーの処理中に例外が発生しました：エラーメッセージ。
* 広告マニフェストURLの広告のプレイリストを取得できませんでした。
* 対象のマニフェストを生成できませんでした。 (HLSManifestResolver)
* 最初の広告呼び出しの応答を解析できませんでした：エラーメッセージ。
* *GET|POST*パスの要求を処理できませんでした：リクエストURL （ライブ/VOD）
* ライブマニフェスト要求を処理できませんでした：リクエストURL （ライブ）
* バリアントマニフェストを返せませんでした：エラーメッセージ。
* グループIDの検証に失敗しました：グループID。
* 生のマニフェストの取得：コンテンツのURL （ライブ）
* VASTリダイレクトに従う：リダイレクトURL。
* 空が見つかりました。 (VOD)
* *数値*&#x200B;広告が見つかりました。 (VOD)
* HTTP要求を受信しました。 （最初のメッセージ）
* 広告の応答時間(*ad response duration *sec)と実際の広告時間(*actual duration *sec)の差が制限を超えているので、広告を無視します。 (HLSManifestResolver)
* ID値が指定されなかった値を無視します。 (GroupAdResolver.java)
* 無効な時間値が指定された値を無視します：*time *for availId = avail ID.
* 無効な期間値が指定された値を無視します：*duration *for availId = avail ID.
* 新しいセッションを初期化します。 （バリアント）
* 無効なHTTPメソッドです。 GETにする必要があります。 (VOD)
* 無効なHTTPメソッドです。 トラッキングリクエストはGETである必要があります。 （ライブ）
* 無効なURL要求されたURLエラーメッセージです。 （バリアント）
* 無効なグループです。 (HLSManifestResolver)
* 無効な要求です。 キャプションは有効な追跡リクエストではありません。 (VOD)
* 無効な要求です。 キャプションの要求は、セッションの確立後に行う必要があります。 (VOD)
* 無効な要求です。 トラッキングリクエストは、セッションの確立後に行う必要があります。 (VOD)
* オーバーロードグループIDに対する無効なサーバーインスタンス：グループID。 （ライブ）
* VASTリダイレクトの制限に達しました — 数値。
* 広告の呼び出し：広告呼び出しのURL。
* 次のマニフェストが見つかりません：コンテンツのURL （ライブ）
* 有効なIDに一致する値が見つかりません：を使用します。 (HLSManifestResolver)
* 再生セッションが見つかりません。 (HLSManifestResolver)
* マニフェストコンテンツURLに対するVODリクエストを処理しています。
* バリアントを処理中です。
* マニフェストコンテンツURLのキャプション要求を処理しています。
* トラッキングリクエストを処理しています。 (VOD)
* リダイレクト広告の応答が空です。 (VASTStAX)
* リクエスト：URL。
* 再生セッションが見つからなかったため、GETリクエストに対するエラー応答を返します。 (VOD)
* 内部サーバーエラーが原因で、GETリクエストに対するエラー応答を返します。
* 無効なアセットを指定したGET要求に対するエラー応答を返す：広告リクエストID。 (VOD)
* 無効または空のグループIDを指定したGET要求に対するエラー応答を返す：グループID。 (VOD)
* 無効な追跡位置の値を指定したGETリクエストに対するエラー応答を返します。 (VOD)
* 無効な構文 — リクエストURLを含むGETリクエストに対するエラー応答を返します。 （ライブ/VOD）
* サポートされていないHTTPメソッドを使用した要求に対するエラー応答を返します：GET|POST。 （ライブ/VOD）
* キャッシュからマニフェストを返しています。 (VOD)
* サーバーが過負荷の状態です。 広告ステッチ要求なしで続行します。 （バリアント）
* 対象のマニフェストを生成中に開始が発生しました。 (HLSManifestResolver)
* 次からバリアントマニフェストを生成中に開始が発生しました：コンテンツのURL （バリアント）
* 開始が広告をマニフェストにステッチしています。 (VODHLSResolver)
* `HH:MM:SS`で広告をステッチしようとしています：AdPlacement \[adManifestURL= ad Manifest URL, durationSeconds= seconds, ignore= ignore, redirectAd= redirect ad, priority= priority.\] \(HLSManifestResolver\)
* pttimelineが無効なため、広告を取得できません — 広告のないコンテンツを返しました。 (VOD)
* 広告を取得できません — 広告のないコンテンツを返しました。 (VOD)
* 広告のクエリを取得できず、コンテンツURLが指定されませんでした。 (VOD)
* 受け取った有効なURL。 （VOD/バリアント）
* バリアントM3U8が見つかりません。 （バリアント）

### TRACE_PLAYBACK_PROGRESSレコード{#trace-playback-progress-records}

マニフェストサーバーは、サーバー側のトラッキングワークフロー中に再生進行に関するシグナルを受け取ると、この種のレコードを生成します。 `TRACE_PLAYBACK_PROGRESS`より後のフィールドは、表に示された順に表示され、タブで区切られます。

| フィールド | タイプ | 説明 |
|---|---|---|
| status | string | HTTPステータスコード |
| 帯域幅 | integer | ストリームの帯域幅 |
| ポイント | integer | ストリーム内のPTS時間 |
| ms_time | integer | マニフェストサーバーがトラッキングURLを生成した時間 |
| url | string | リダイレクトURL |
| **¿** header_user_agent | string | HTTP User-Agentヘッダー |
| **¿** header_dnt | integer | HTTP追跡しないヘッダー |
| **¿** effective_remote_address | string | IPv4有効リモートアドレス |
| **¿** remote_address | string | IPv4リモートアドレス |

**最¿後の4つ** のフィールドはオプションです。

## マルチビットレートストリーム{#multiple-bitrate-streams}

広告挿入のクライアントリクエストは、通常、バリアントM3U8形式のプレイリストに複数のビットレートを指定します。 マニフェストサーバーは、ビットレートごとに別々のM3U8リンクを含む新しいバリアントM3U8ファイルを生成して返します。 また、これらのM3U8を結び付けるための一意のグループIDも生成されます。

マニフェストサーバーは、クライアントのBootstrapURL要求の情報を使用して、コンテンツバリアントプレイリストを取得します。 ストリームレベルのコンテンツへのマニフェストサーバーリンクを含む新しいバリアントプレイリストを生成します。 クライアントは、これらを使用して広告挿入リクエストを作成します。 マニフェストサーバーのストリームレベルコンテンツリンクの形式は次のとおりです。

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/**
vodマニフェストサーバーは、コンテンツのプレイリストタイプに基づいてこの値を設定します。ライブ/リニア(
`#EXT-X-PLAYLIST-TYPE:EVENT`)またはVOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* ****
publisherAssetIDPublisherのBootstrapURL要求で提供される特定のコンテンツの一意のID。

* ****
レンディションマニフェストサーバーは、 
`BANDWIDTH` の値を指定し、それを使用して広告のビットレートとコンテンツのビットレートを一致させます。広告のビットレートは、最も低いビットレートの広告レンディションがそうしない限り、コンテンツのビットレートを超えることはできません。

* **groupIDTマニフェストサーバーはこの値を生成し、それを使用して、クライアントが広告をリクエストするビットレートレンディションに関係なく、広告の配置を一貫性のあるものにします。**


* **base64エンコードされたビットレート**
ストリームのURLマニフェストサーバーURLセーフベース64は、コンテンツストリームの絶対URLをエンコードします。各ストリームには、独自のURLがあります。

* **クエリ**
パラメーターBootstrapURLリクエストで指定されるクエリパラメーター。
