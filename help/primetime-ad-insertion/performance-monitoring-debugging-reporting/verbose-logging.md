---
title: 詳細ログ
description: 詳細ログ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 0%

---

# 詳細ログ {#verbose-logging}

## ptdebug/logging イベントの説明 {#ptdebug-logging-events}

マニフェストサーバーセッションのデバッグログを開始する際に、 `ptdebug` パラメーターをリクエスト URL に追加して、マニフェストサーバーが HTTP ヘッダーで返す情報に関する次のオプションを指定します。

* `ptdebug=true`
TRACE_HTTP_HEADER を除くすべてのレコードと、TRACE_AD_CALL レコードからのほとんどの呼び出し/応答データ。

* `ptdebug=AdCall`
TRACE_AD_タイプ ( 例えば、TRACE_AD_CALL) のみが記録されます。

* `ptdebug=Header`
TRACE_HTTP_HEADER レコードのみ。

## ログレコードの形式 {#log-record-formats}

各ログレコードにはタイプとフィールドのセットがあり、一部はオプションです。 レコードタイプまでのすべてのレコードのフィールドは同じです。 タイムスタンプとセッションに関する情報が提供されます。 レコードタイプは、ログに記録されるイベントの種類を識別し、後続のフィールドは、ログに記録されたイベントに関する情報を提供します。

ログレコードの構造は次のとおりです。

`datetime request_id session_id zone_id record_type other fields`.

| フィールド | タイプ | 説明 |
|---|---|---|
| 日時 | 文字列 | タイムスタンプ |
| request_id | 文字列 | マニフェストサーバーで使用されるリクエスト ID （UNIX タイムスタンプ） |
| session_id | 文字列 | マニフェストサーバーが使用するセッション ID |
| zone_id | 整数 | ゾーン |
| record_type | 文字列 | ログに記録されるイベントのタイプ |
| その他のフィールド | 変化 | イベントのタイプに依存 |

このタイプのレコードは、HTTP リクエストの結果を記録します。 超えるフィールド `TRACE_REQUEST_INFO` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | 返された HTTP ステータスコード |
| request_method | 文字列 | HTTP メソッド (GETまたはPOST) |
| request_uri | 文字列 | HTTP リクエスト URI （ホストなし） |
| request_length | 整数 | リクエストの長さ（バイト） |
| response_length | 整数 | 応答の長さ（バイト） |
| デルタ | 整数 | リクエストを処理する時間（ミリ秒） |
| module_type | 文字列 | バリアント、ストリーム、VOD のいずれか |
| remote_address_aud_client_ip | 文字列 | **‡** |
| remote_address_x_fwd_for_hdr_key | 文字列 | **‡** |
| remote_host_port | 文字列 | **‡** |

**‡** 最後の 3 つのフィールドはオプションです。

**例**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER レコード {#trace-http-header-records}

このタイプのレコードは、マニフェストサーバーとクライアント、広告サーバー、またはコンテンツサーバーとの間で HTTP 呼び出し中に交換された HTTP ヘッダーをログに記録します。 TRACE_HTTP_HEADER を超えるフィールドは、表に示す順序でタブで区切られて表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| request_type | 文字列 | リクエストのタイプ（MAIN または UNKNOWN） |
| request_response | 文字列 | 応答ヘッダー（リクエストまたは応答） |
| header_name | 文字列 | HTTP ヘッダー名 |
| header_value | 文字列 | Base64 でエンコードされた HTTP ヘッダー値 |

>[!NOTE]
>
>The `request_type` および `header_value` フィールドはオプションです。

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

### TRACE_AD_CALL レコード {#tracing-ad-call-records}

このタイプのレコードは、マニフェストサーバー広告リクエストの結果をログに記録します。 超えるフィールド `TRACE_AD_CALL` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | 返された HTTP ステータスコード |
| request_duration | 整数 | リクエストから応答までの時間（ミリ秒） |
| ad_server_query_url | 文字列 | 広告呼び出しの URL （クエリパラメーターを含む） |
| ad_system_id | 文字列 | 広告サーバー応答からの広告システム ( 指定されていない場合のAuditude) |
| avail_id | 文字列 | コンテンツマニフェストファイルの広告キューからの利用可能な ID（VOD の場合はなし） |
| avail_duration | 数値 | コンテンツマニフェストファイル内の広告キューからの利用時間（秒）（VOD の場合はなし） |
| ad_server_response | 文字列 | 広告サーバーからの Base64 エンコードされた応答 |

例：

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT、TRACE_AD_RESOLVE およびTRACE_AD_REDIRECT のレコード {#trace-ad-insert-resolve-redirect}

このタイプのレコードは、レコードタイプが示す広告リクエストの結果をログに記録します。 レコードタイプ以外のフィールドは、テーブル内のタブで区切られた順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | HTTP ステータスコードを返しました。 |
| avail_id | 文字列 | コンテンツマニフェストファイル（ライブ）内の広告キューまたはマニフェストサーバー (VOD) からの、利用可能な ID。 |
| ad_type | 文字列 | 広告のタイプ（DIRECT または REDIRECT）。 |
| ad_duration | 整数 | 広告サーバー応答からの広告の時間（秒）。 |
| ad_content_url | 文字列 | 広告サーバー応答からの広告のマニフェストファイルの URL。 |
| **†** ad_content_url_actual | 文字列 | 挿入された広告のマニフェストファイルの URL。 TRACE_AD_REDIRECT の場合は空です。 |
| ad_system_id | 文字列 | 広告サーバー応答からの広告システム ( 指定されていない場合のAuditude)。 |
| ad_id | 文字列 | 広告サーバー応答からの広告の ID。 |
| creative_id | 文字列 | 広告サーバー応答からのクリエイティブの ID（広告ノードから）。 |
| **†** ad_call_id | 文字列 | 未使用。 将来の使用のために予約されています。 |
| デルタ | 整数 | このイベントに費やされた時間（ミリ秒）。 |
| **†** misc | 文字列 | 広告がスキップされた理由。 |

**†** `ad_content_url_actual`, `ad_call_id`、および `misc` フィールドはオプションです。

>[!NOTE]
>
>の場合 `TRACE_AD_RESOLVE` および `TRACE_AD_INSERT`:URL を `ad_content_url_actual` フィールドは、トランスコードされた広告（使用可能な場合）用です。 それ以外の場合、フィールドは空です。 `TRACE_AD_RESOLVE` または `ad_content_url` 対象： `TRACE_AD_INSERT`.

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

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE レコード {#trace-transcoding-no-media-to-transcode}

このタイプのレコードは、見つからない広告クリエイティブをログに記録します。 その向こうの唯一のフィールド `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE` がテーブルに表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ad_id | 文字列 | 完全修飾広告 ID (FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\] \] Q_AD_ID: PROTOCOL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \] プロトコル：AUDITUDE,VAST) |

このタイプのレコードは、マニフェストサーバーが CRS に送信するトランスコードリクエストの結果をログに記録します。 超えるフィールド `TRACE_TRANSCODING_REQUESTED` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ad_id | 文字列 | 完全修飾広告 ID |
| ad_manifest_url | 文字列 | 広告サーバー応答からの広告のマニフェストファイルの URL |
| creative_type | 文字列 | メディアのタイプ |
| flags | 文字列 | ID3 は、トランスコードリクエストに ID3 タグの追加リクエストが含まれているかどうかを示します |
| target_duration | 文字列 | トランスコードされたクリエイティブのターゲット時間（秒） |

このタイプのレコードは、サーバー側トラッキングを実行するリクエストを示します。 超えるフィールド `TRACE_TRACKING_REQUEST` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| tracking_url_count | 整数 | トラッキング URL の数 |
| 開始 | float | PTS フラグメントの開始時間（ミリ秒の精度で秒） |
| 終了 | float | PTS フラグメントの終了時間（ミリ秒の精度で秒） |

このタイプのレコードは、サーバー側トラッキングのトラッキング URL を提供します。 超えるフィールド `TRACE_TRACKING_REQUEST_URL` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| timestamp | float | 再生セッション内の、トラッキング URL への ping 送信までの時間（秒、精度は。001）。 |
| ad_system | 文字列 | 広告システム（例：auditude） |
| url | 文字列 | ping への URL |

マニフェストサーバーが対しておこなうこのタイプのログのレコード `WEBVTT` キャプション。 超えるフィールド `TRACE_WEBVTT_REQUEST` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | 返された HTTP ステータスコード |
| vtt_uri | 文字列 | リクエストの URL |
| 開始 | float | 分割開始時間（秒、ミリ秒の精度） |
| 終了 | float | 分割終了時間（ミリ秒の精度で秒） |

このタイプのログのレコードは、マニフェストサーバーがでクライアントに送信する応答を記録します。 `answer` ～を求める `WEBVTT` キャプション。 超えるフィールド `TRACE_WEBVTT_RESPONSE` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | 返された HTTP ステータスコード |
| 応答 | 文字列 | Base64 でエンコードされた応答がクライアントに送信されました |

このタイプのレコードは、マニフェストサーバーが行う要求に対する応答をログに記録します。 `WEBVTT` キャプション。 超えるフィールド `TRACE_WEBVTT_SOURCE` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | 返された HTTP ステータスコード |
| ソース | 文字列 | Base64 でエンコードされた元の VTT コンテンツ |

このタイプのレコードを使用すると、マニフェストサーバーは、広告の取り込み時に他に予定されていないイベントと情報をログに記録できます。 その向こうのフィールド `TRACE_MISC` は、メッセージ文字列で構成されます。 表示される可能性のあるメッセージには、次のものが含まれます。

* 無視された広告： AdPlacement \[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb....m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= seconds, ignore= ignore, redirectAd= redirectAd, priority= priority
* 広告の配置が null を返しました。
* 広告が正常にステッチされました。
* 広告呼び出しが失敗しました：エラーメッセージ。
* 生のマニフェストを取得する User-Agent を追加しています： user-agent。
* 生のマニフェストを取得するための cookie の追加：#
* 無効な URL リクエスト URL エラーメッセージです。 （バリアント URL の解析に失敗しました）
* URL を呼び出しました： URL が戻り値：応答コードを取得しました。 （ライブ URL）
* URL を呼び出しました。リターンコード：レスポンスコード。 (VOD URL)
* 広告の解決中に競合が見つかりました。ミッドロール開始またはミッドロール終了のいずれかが、ミッドロール (VOD) に含まれるプリロールまたはプリロール内に含まれます。
* URI：リクエスト URL のハンドラーによってスローされた未処理の例外が検出されました。
* バリアントマニフェストの生成が完了しました。 （バリアント）
* バリアントマニフェストの生成が完了しました。
* VAST リダイレクト*リダイレクト URL *error：エラーメッセージの処理時の例外。
* 広告マニフェスト URL の広告のプレイリストを取得できませんでした。
* ターゲットのマニフェストを生成できませんでした。 (HLSManifestResolver)
* 最初の広告呼び出し応答を解析できませんでした：エラーメッセージ。
* パス：リクエスト URL の*GET|POST*リクエストを処理できませんでした。 （ライブ/VOD）
* ライブマニフェストリクエストを処理できませんでした：リクエスト URL。 （ライブ）
* バリアントマニフェストを返せませんでした：エラーメッセージ。
* グループ ID ：グループ ID を検証できませんでした。
* 生のマニフェストを取得しています：コンテンツの URL。 （ライブ）
* VAST リダイレクトの次：リダイレクト URL。
* 空の値が見つかりました。 (VOD)
* 見つかりました *数値* 広告。 (VOD)
* HTTP リクエストを受信しました。 （最初のメッセージ）
* 広告の応答時間（*広告の応答時間*秒）と実際の広告時間（*実際の時間*秒）の差が制限を超えているので、広告は無視されます。 (HLSManifestResolver)
* ID 値が指定されなかった利用を無視します。 (GroupAdResolver.java)
* 無効な時間値：availId = avail ID の*time *を提供した利用を無視します。
* 無効な期間の値を提供した利用状況を無視します： availId =利用可能な ID の場合： *duration *
* 新しいセッションを初期化します。 （バリアント）
* 無効な HTTP メソッドです。 GET。 (VOD)
* 無効な HTTP メソッドです。 トラッキングリクエストは、GETである必要があります。 （ライブ）
* 無効な URL リクエスト URL エラーメッセージです。 （バリアント）
* 無効なグループです。 (HLSManifestResolver)
* 無効なリクエストです。 キャプションは有効な追跡リクエストではありません。 (VOD)
* 無効なリクエストです。 キャプションリクエストは、セッションの確立後におこなう必要があります。 (VOD)
* 無効なリクエストです。 トラッキングリクエストは、セッションの確立後におこなう必要があります。 (VOD)
* オーバーロードグループ ID ：グループ ID のサーバーインスタンスが無効です。 （ライブ）
* VAST リダイレクトの上限に達しました — 数。
* 広告呼び出し：広告呼び出しの URL を作成しています。
* 次のコンテンツ URL のマニフェストが見つかりません。 （ライブ）
* 利用可能 ID：利用可能 ID に一致する利用可能な情報が見つかりません。 (HLSManifestResolver)
* 再生セッションが見つかりません。 (HLSManifestResolver)
* マニフェストコンテンツ URL の VOD リクエストを処理しています。
* 処理バリアント。
* マニフェストコンテンツ URL のキャプションリクエストを処理しています。
* トラッキングリクエストを処理しています。 (VOD)
* リダイレクト広告の応答が空です。 (VASTStAX)
* リクエスト： URL。
* 再生セッションが見つからなかったので、GETリクエストに対するエラー応答を返す。 (VOD)
* 内部サーバーエラーが原因で、GETリクエストに対するエラー応答を返す。
* 無効なアセットを指定したGETリクエストに対するエラー応答を返す：広告リクエスト ID。 (VOD)
* 無効または空のグループ ID を指定するGETリクエストに対するエラー応答を返す：グループ ID。 (VOD)
* 無効な追跡位置値を指定するGETリクエストのエラー応答を返します。 (VOD)
* 無効な構文のGETリクエストに対するエラー応答を返します — リクエスト URL。 （ライブ/VOD）
* サポートされていない HTTP メソッドを使用してリクエストのエラー応答を返します：GET|POST。 （ライブ/VOD）
* キャッシュからマニフェストを返す。 (VOD)
* サーバーが過負荷状態です。 広告ステッチリクエストを使用せずに続行します。 （バリアント）
* ターゲットのマニフェストの生成を開始します。 (HLSManifestResolver)
* 次のコンテンツ URL からバリアントマニフェストの生成を開始します。 （バリアント）
* 広告をマニフェストにステッチし始めます。 (VODHLSResolver)
* で広告をステッチしようとしています `HH:MM:SS`: AdPlacement \[adManifestURL= ad Manifest URL, durationSeconds= seconds, ignore= ignore, redirectAd= redirect ad, priority= priority.\] \(HLSManifestResolver\)
* 無効な pttimeline のため、広告を取得できません。広告のないコンテンツを返しました。 (VOD)
* 広告を取得できません — 広告のないコンテンツを返しました。 (VOD)
* 広告クエリを取得できず、コンテンツ URL が指定されていません。 (VOD)
* 有効な URL を受け取りました。 （VOD/バリアント）
* バリアント M3U8 が見つかりません。 （バリアント）

### TRACE_PLAYBACK_PROGRESS レコード {#trace-playback-progress-records}

マニフェストサーバーは、サーバー側トラッキングワークフロー中に再生の進行に関するシグナルを受け取ると、この種のレコードを生成します。 超えるフィールド `TRACE_PLAYBACK_PROGRESS` は、タブで区切られた表内の順序で表示されます。

| フィールド | タイプ | 説明 |
|---|---|---|
| ステータス | 文字列 | HTTP ステータスコード |
| 帯域幅 | 整数 | ストリームの帯域幅 |
| ポイント | 整数 | ストリーム内の PTS 時間 |
| ms_time | 整数 | マニフェストサーバーがトラッキング URL を生成した時間 |
| url | 文字列 | リダイレクト URL |
| **¿** header_user_agent | 文字列 | HTTP User-Agent ヘッダー |
| **¿** header_dnt | 整数 | HTTP do-not-track ヘッダー |
| **¿** effective_remote_address | 文字列 | IPv4 の有効なリモートアドレス |
| **¿** remote_address | 文字列 | IPv4 リモートアドレス |

**¿** 最後の 4 つのフィールドはオプションです。

## 複数ビットレートストリーム {#multiple-bitrate-streams}

広告挿入に対するクライアント要求では、通常、バリアント M3U8 形式のプレイリストで複数のビットレートを指定します。 マニフェストサーバは、ビットレートごとに別々の M3U8 リンクを含む新しいバリアント M3U8 ファイルを生成して返します。 また、これらの M3U8 を結び付けるために一意のグループ ID が生成されます。

マニフェストサーバーは、クライアントのBootstrapURL リクエストの情報を使用して、コンテンツバリアントプレイリストを取得します。 マニフェストサーバーからストリームレベルのコンテンツへのリンクを含む新しいバリアントプレイリストが生成されます。 クライアントは、これらを使用して、広告挿入リクエストを作成します。 マニフェストサーバーのストリームレベルのコンテンツリンクの形式は次のとおりです。

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/vod**
マニフェストサーバーは、コンテンツのプレイリストタイプ（ライブ/リニア）に基づいてこの値を設定します (`#EXT-X-PLAYLIST-TYPE:EVENT`) または VOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* **publisherAssetID**
BootstrapURL リクエストで提供される特定のコンテンツに対するパブリッシャーの一意の ID。

* **rendition**
マニフェストサーバーは、 `BANDWIDTH` コンテンツストリームの値。広告のビットレートとコンテンツのビットレートを照合するために使用されます。 広告ビットレートが最も低い広告レンディションがそのようにしない限り、広告ビットレートがコンテンツのビットレートを超えることはできません。

* **groupID**
マニフェストサーバーは、この値を生成し、それを使用して、クライアントが広告を要求するビットレートレンディションに関係なく、一貫した広告の配置を確保します。

* **ビットレートストリームの base64 エンコードされた url**
マニフェストサーバ URL セーフベース 64 は、コンテンツストリームの絶対 URL をエンコードする。 各ストリームには独自の URL があります。

* **クエリパラメーター**
クエリ URL リクエストで指定されたBootstrapーパラメーター。
