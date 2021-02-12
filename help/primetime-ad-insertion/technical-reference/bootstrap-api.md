---
title: BootstrapAPI
description: 'BootstrapAPI '
translation-type: tm+mt
source-git-commit: bf99c76bbbb67560adc675cf84297b8d3b04e19d
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---


# BootstrapAPI {#bootstrap-api}

BootstrapAPIは、通常、クライアント/ビデオ再生APIに送信されるURLです。  設定できるオプションとパラメーターについては、[BootstrapAPIパラメーター](#bootstrap-api-parameters)を参照してください。

## マニフェストサーバーにコマンドを送信{#send-a-command-to-the-manifest-server}

1. 次のパターンを使用して構築されたブートストラップURLに対して`HTTP GET`リクエストを送信します。

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **ファイル** 拡張子Defined。`.m3u8` ターゲットマニフェストがHLSの場合、ターゲットマニフェスト `.mpd` がDASH内にある場合。

   * **PublisherAssetIDR** が必要です。特定のコンテンツに対する発行者の一意のID。

   * **コンテンツ** URLRが必要です。コンテンツM3U8ファイルのURL。マニフェストサーバーURL内で安全であるようにエンコードされたBase64。 ビットレートストリームが1つだけの場合でも、コンテンツURLはバリアントM3U8ファイルを指す必要があります。

   * **クエリ** パラメーターこれらは、リクエストの中で最も多様な部分を構成します。どの種類のクライアントがリクエストを行っているか、およびマニフェストサーバーに何をして欲しいかをマニフェストサーバーに伝えます。

   例：

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTPリクエストとHTTPSリクエスト**

   マニフェストサーバーは、クライアントのリクエストと同じHTTPプロトコルを使用してURLを作成します。 プレーヤーが安全でないHTTP(http)リクエストを行った場合、マニフェストサーバーは、httpプロトコルを使用してマニフェストURLとAuditudeトラッキングURLを返します。 プレーヤーが安全なHTTP(https)接続、マニフェストサーバーを行うと、httpsプロトコルを使用してマニフェストURLとAuditudeトラッキングURLを返します。

   >[!NOTE]
   >
   >マニフェストサーバーは、サードパーティのトラッキングビーコンのプロトコル（HTTPまたはHTTPS）を変更できません。 目的のプロトコルを設定するには、コンテンツおよびサードパーティの広告プロバイダーに問い合わせる必要があります。  セグメントURLプロトコルは変更できますが、デフォルトでは、ターゲットマニフェストで定義されているのと同じプロトコルを使用します。

## BootstrapAPIパラメータ{#bootstrap-api-parameters}

クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、そのクライアントがマニフェストサーバーに何を求めているかを伝えます。 必須の形式や値が必要な場合もあります。
完全なURLは、ベースURLの後に疑問符が続き、`parameterName=value`引数がアンパサンドで区切られて構成されます。 例：`Base URL?name1=value1&name2=value2& . . .&name n=value n`。

マニフェストサーバーは、以下のパラメーターを認識します。 すべてのクエリ文字列\
パラメーターが広告サーバーに渡されます。

| parameter | description | 形式 |
|---|---|---|
| _sid_ | マニフェストサーバーがセッションIDの生成に使用する一意のID。 | DASH/HLSの両方に必須 |
| live | 渡されたコンテンツ項目がライブストリームであることをPrimetimeAd Insertionに通知します。  このパラメーターが渡されない場合、Primetime Ad挿入は、マニフェストがライブかvodかを判断するために、最初のマニフェスト呼び出しでセカンダリリクエストを行います。<br>使用可能な値：<br>true(ライブ<br>コンテンツの場合)、<br>vodコンテンツの場合、自動検出のためのtrue(true) | HLSの場合はオプションです。  DASHに必須 |
| z | PrimetimeAd Insertionに指定する必要があるアセットのゾーンID。 お客様のAdobeテクニカルアカウントマネージャが提供します。 | DASH/HLSの両方に必須 |
| pabimode | ライブストリームに対して[部分的な広告ブレーク挿入](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support)を有効にします。<br>使用可能な値：<br>trueを指定すると、無効にする（デフォルトは無効）<br>を有効にします。 | HLS/DASH |
| ptadtimeout | ダウンストリームプロバイダーの応答に時間がかかりすぎる場合に、広告の全体的な解決時間を制限できるようにします。  長時間にわたる応答が再生に問題を引き起こす可能性があるので、Primetime DAIは特定の時間制限内に応答を強制できます。<br>使用可能な値：ミリ秒単位の<br>数値文字列。<br>無効にする場合は省略（デフォルトは無効） | HLS/DASH |
| ptadwindow | ルックバック広告判定時間の長さ（秒）。DVRユーザーがストリームに参加したときに、PrimetimeAd Insertionが広告キューを探す時間（秒）です。 値をゼロにすると、最初のマニフェスト内のミッドロール広告判定が無効になり、最初の更新後にのみ判定が再開されます。 このパラメーターは、数秒間しか続かないセッション(チャネルのフリップなど)への広告挿入を無効にする場合に便利です。<br>使用可能な値：<br>数値文字列0 ～ 1800（デフォルトは1800） | HLSのみ |
| ptassetid | 投稿者によって割り当てられ、管理されるコンテンツの一意のIDです。  Akamai Ad Scalerと組み合わせて使用する場合は必須です。 | HLS/DASH |
| ptcdn | トランスコードされたアセットをホストするための1つ以上のCDNのリスト。 詳しくは、[配信とストレージ](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md)を参照してください。<br>使用可能な値：<br>akamai、level3、lnw(limelight networks)、comcast。<br>デフォルトでは、PrimetimeAd InsertionCDNが使用されます。 | HLS/DASH |
| ptcueformat | ad decisioningを実行するために指定した形式（scte35など）。<br>使用可能な値：<br>dpisimple、dpiscte35、<br>elementalカスタムキュー形式の場合は、ユースケースで使用する値について、テクニカルアカウント担当者にお問い合わせください | HLS/DASH |
| ptfailover | マスタープレイリストで指定されているプライマリストリームとフェイルオーバーストリームを識別し、それらを別々のセットとして扱うようマニフェストサーバーに通知します。 これにより、フェイルオーバーが容易になり、タイミングエラーが発生するのを防ぎます。 （Apple HLSデバイスのみ） 詳しくは、[HLSプレーヤーの切り替えの容易化](hls-switching-to-failover.md)を参照してください。 | HLSのみ |
| ptmulticall | 有効にした場合、VODアセット内の各アバイルに対して個別の広告リクエストが行われます。  デフォルトでは、PrimetimeAd Insertionは、利用可能なすべての情報を収集し、それを1回のリクエストで広告サーバーに送信しようとします。 使用可能な値：有効にする場合はtrue、無効にする場合は<br>omit（デフォルトは無効） | HLS/DASH |
| ptparallelstream | CMAFのデミュックスオーディオまたはビデオストリームを並行してリクエストするプレーヤーを持つお客様は、オーディオとビデオトラックの広告の一貫性を確保できます。 | HLSのみ |
| ptprotoswitch | 名前付きマニフェストの書き直しルールと広告取得ルールを有効にします。このルールは通常、テクニカルサポート担当者が設定します。<br>例：adfetch_fw、cdn_akm | HLS/DASH |
| pttagds | HLSヘッダにEXT-X-DISCONTINUITY-SEQUENCEタグを挿入できます。可能な値：trueは無効にする（デフォルト無効）を有効にします。 | HLSのみ |
| pttimeline | 広告を配置したいタイムラインとコンテンツを含む文字列。コンテンツストリーム内の広告の時間を上書きします。 [ VODタイムラインの形式を参照してください。  ] | HLS/DASH |
| pttoken | CDNに対するコンテンツフラグメント/セグメント認証トークン保護スキームを有効にします<br>可能な値：<br>akamai, lnw (limelight), ctl (centurylink)（デフォルトのトークン化は無効です） | HLS/DASH |
| pttrackingmode | 広告トラッキングスキームを有効にします。<br>使用可能な値：サーバー側広告トラッキングの<br>単純なクライアント側広告<br><br>トラッキングサーバー側広告トラッキングサーバー側広告トラッキングの単純なクライアント/サーバーハイブリッド広告トラッキングの場合（デフォルトでは、広告トラッキングは実行されません） | HLS/DASH |
| pttrackingposition | マニフェストサーバーに対して、広告トラッキング情報のみを返すように指示します。 このパラメーターはブートストラップ要求に指定しないでください。<br>注意：マニフェストサーバーは、渡された値をすべて無視します。ただし、nullまたは空の文字列を渡すと、マニフェストサーバーはM3U8を返します | HLS/DASH<br>クライアント側トラッキング |
| pttrackingversion | 返す形式のバージョンを設定します。<br>使用可能な値：<br>v1、v2、v3またはvmap | HLS/DASH<br>クライアント側トラッキング |
| scteTracking | このパラメーターは、プレーヤーがM3U8をフェッチする際にSCTEタグ情報の取得が必要であることをマニフェストサーバーに示します。<br>使用可能な値：<br>trueまたはfalse（デフォルトはfalse）<br>注意：SCTE-35データは、クエリパラメーターの値を次のように組み合わせてJSONサイドカーで返されます。<br>ptcueformat=turner | 元素 | nfl | DPIScte35<br>pttrackingversion=v2<br>scteTracking=true<br> | HLSのみ |
| vetargetmultiplier | ライブポイントからのセグメント数プリロールオフセットは、次を使用して設定されます。( vetargetmultiplier * targetduration ) + vebufferlength<br>注意：このパラメーターは、Live/Linear HLSストリームにのみ適用されます<br>可能な値：<br>数値浮動小数点<br>(デフォルト：3.0 - HLS仕様と同じ) | HLSのみ |
| vebufferLength | ライブポイントからの秒数。vetargetmultiplierと組み合わせて使用します。<br>注意：このパラメーターは、ライブ/リニアHLSストリーム<br>にのみ適用されます。可能な値：<br>数値浮動小数点<br>(デフォルト：3.0) | HLSのみ |
