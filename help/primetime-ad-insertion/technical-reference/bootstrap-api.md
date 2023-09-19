---
title: BootstrapAPI
description: BootstrapAPI
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# BootstrapAPI {#bootstrap-api}

BootstrapAPI は、通常、クライアント/ビデオ再生 API に送信される URL です。  設定可能なオプションとパラメーターについては、 [BootstrapAPI パラメーター](#bootstrap-api-parameters).

## マニフェストサーバーにコマンドを送信する {#send-a-command-to-the-manifest-server}

1. を送信します。 `HTTP GET` 次のパターンを使用して構築されたブートストラップ URL のリクエスト。

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **ファイル拡張子** 定義済み。 `.m3u8` ターゲットマニフェストが HLS の場合、 `.mpd` ターゲットマニフェストが DASH の場合。

   * **PublisherAssetID** 必須。 特定のコンテンツに対する投稿者の一意の ID。

   * **コンテンツ URL** 必須。 コンテンツ M3U8 ファイルの URL。マニフェストサーバー URL 内で安全にエンコードされる Base64。 ビットレートストリームが 1 つだけの場合でも、コンテンツ URL はバリアント M3U8 ファイルを指している必要があります。

   * **クエリパラメーター** これらは、リクエストの最も様々な部分を構成します。 マニフェストサーバーに対して、どの種類のクライアントがリクエストを実行しているか、およびマニフェストサーバーに何を実行しているかを伝えます。

   例：

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **HTTP リクエストと HTTPS リクエスト**

   マニフェストサーバーは、クライアントの要求と同じ HTTP プロトコルを使用して URL を作成します。 プレーヤーがセキュアでない HTTP(http) リクエストを実行すると、マニフェストサーバーは、http プロトコルを使用してマニフェスト URL とAuditudeトラッキング URL を返します。 プレーヤーが安全な HTTP(https) 接続（マニフェストサーバー）をおこなうと、マニフェスト URL と https プロトコルを使用したAuditudeトラッキング URL を返します。

   >[!NOTE]
   >
   >マニフェストサーバーは、サードパーティのトラッキングビーコンのプロトコル（HTTP または HTTPS）を変更できません。 目的のプロトコルを設定するには、コンテンツやサードパーティ広告プロバイダーに問い合わせる必要があります。  セグメント URL プロトコルは変更できますが、デフォルトでは、ターゲットマニフェストで定義されているのと同じプロトコルを使用します。

## BootstrapAPI パラメーター {#bootstrap-api-parameters}

クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、マニフェストサーバーで実行する必要のある処理を伝えます。 一部は必須で、一部は特定の形式または値を持ちます。
完全な URL は、ベース URL と疑問符が続く形式で構成され、 `parameterName=value` 引数をアンパサンドで区切って指定します。 例： `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

マニフェストサーバーは、次のパラメーターを認識します。 すべてのクエリ文字列\
パラメーターが広告サーバーに渡されます。

| パラメーター | 説明 | 形式 |
|---|---|---|
| _sid_ | マニフェストサーバーがセッション ID の生成に使用する一意の ID。 | DASH/HLS の両方に必須 |
| live | 渡されたコンテンツAd Insertionがライブストリームであることを Primetime 項目に通知します。  このパラメーターが渡されない場合、Primetime Ad insertion は、最初のマニフェスト呼び出しで 2 番目のリクエストを実行し、マニフェストがライブか vod かを判断します。<br>可能な値：<br>ライブコンテンツに対して true<br>vod コンテンツに対する false<br>自動検出用に省略する | HLS の場合はオプションです。  DASH に必須 |
| z | PrimetimeAd Insertionに提供する必要があるアセットのゾーン ID。 担当のAdobeテクニカルアカウントマネージャーが提供します。 | DASH/HLS の両方に必須 |
| pabimode | 有効 [部分的な広告ブレーク挿入](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support) ライブストリームの場合。<br>可能な値：<br>有効にする場合は true<br>無効にする（デフォルトでは無効） | HLS/DASH |
| ptadtimeout | ダウンストリームプロバイダーの応答に時間がかかりすぎる場合に、全体的な広告解決時間を制限できるようにします。  長時間実行された応答が再生に問題を引き起こす可能性があるので、Primetime DAI は特定の時間制限内に応答を強制的に送信します。<br>可能な値：<br>ミリ秒単位の数値文字列。<br>無効にする（デフォルトでは無効） | HLS/DASH |
| ptadwindow | ルックバック広告判定ウィンドウの時間（秒） — DVRAd Insertionがストリームに参加する際に Primetime ユーザーが広告キューを探す距離。 値 0 を指定すると、最初の更新の後にのみ判定が再開され、最初のマニフェストのミッドロール広告判定が無効になります。 このパラメーターは、数秒間しか持続しないセッション（チャネルの反転）への広告挿入を無効にする場合に役立ちます。<br>可能な値：<br>数値文字列 0 ～ 1800 （デフォルトは 1800） | HLS のみ |
| ptassetid | 投稿者によって割り当てられ、管理されるコンテンツの一意の ID。  Akamai Ad Scaler と組み合わせて使用する場合は必須です。 | HLS/DASH |
| ptcdn | トランスコードされたアセットをホストする 1 つ以上の CDN のリスト。 詳しくは、 [配信とストレージ](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md).<br>可能な値：<br>akamai、level3、llnw(limelight networks)、comcast。<br>デフォルトでは、PrimetimeAd InsertionCDN が使用されます。 | HLS/DASH |
| ptcueformat | 広告判定を実行するタグの指定された形式（例：scte35）。<br>可能な値：<br>dpisimple, dpiscte35, elemental<br>カスタムキュー形式の場合、使用例に使用する値については、テクニカルアカウント担当者にお問い合わせください | HLS/DASH |
| ptfailover | マニフェストサーバーに対して、マスタープレイリストで指定されたプライマリストリームとフェイルオーバーストリームを識別し、それらを別々のセットとして扱うよう通知します。 これにより、フェイルオーバーが容易になり、タイミングエラーが発生するのを防ぎます。 (Apple HLS デバイスのみ ) 詳しくは、 [HLS プレーヤーの切り替えの容易化](hls-switching-to-failover.md) | HLS のみ |
| ptmulticall | 有効にした場合、VOD アセット内の各メールに対して個別の広告リクエストがおこなわれます。  デフォルトでは、PrimetimeAd Insertionは、利用可能なすべての情報を収集し、1 回のリクエストで広告サーバーに送信しようとします。 可能な値：true を指定して有効にする、 <br>無効にする（デフォルトでは無効） | HLS/DASH |
| ptparallelstream | CMAF のデミュックス済みオーディオまたはビデオストリームを同時にリクエストするプレーヤーを持つお客様が、オーディオおよびビデオトラック内の広告の一貫性を確保できます。 | HLS のみ |
| ptprotoswitch | 名前付きマニフェストの書き直しルールおよび広告取得ルールを有効にします。これは通常、テクニカルサポート担当者が設定します。<br>例： adfetch_fw, cdn_akm | HLS/DASH |
| pttagds | HLS ヘッダーへの EXT-X-DISCONTINUITY-SEQUENCE タグの挿入を有効にします。可能な値：無効にする（デフォルトで無効）には true を指定します。 | HLS のみ |
| pttimeline | コンテンツストリーム内の広告の時間を上書きする、広告の配置とコンテンツに必要なタイムラインを含む文字列。 [VOD タイムライン形式を参照してください] | HLS/DASH |
| ptoken | CDN のコンテンツフラグメント/セグメント認証トークン保護スキームを有効にします。<br>可能な値：<br>akamai、lnw(limelight)、ctl(centurylink)（デフォルトのトークン化は無効） | HLS/DASH |
| pttrackingmode | 広告トラッキングスキームを有効にします。<br>可能な値：<br>クライアント側の広告トラッキングに適した<br>サーバーサイド広告トラッキング用の sstm<br>ハイブリッドクライアント/サーバー広告トラッキングのシンプルな（デフォルトでは、広告トラッキングは実行されません） | HLS/DASH |
| pttrackingposition | マニフェストサーバーに対して、広告トラッキング情報のみを返すように指示します。 ブートストラップリクエストでは、このパラメーターを指定しないでください。<br>注意：マニフェストサーバーは渡された値をすべて無視します。 ただし、null または空の文字列を渡すと、マニフェストサーバーは M3U8 を返します | HLS/DASH<br>クライアント側トラッキング |
| pttrackingversion | 返す形式のバージョンを設定します。<br>可能な値：<br>v1、v2、v3、または vmap | HLS/DASH<br>クライアント側トラッキング |
| scteTracking | このパラメーターは、M3U8 を取得するプレーヤーが SCTE タグ情報を取得する必要があることをマニフェストサーバーに示します。<br>可能な値：<br>true または false （デフォルトは false）<br>注意： SCTE-35 データは、次のクエリパラメーター値の組み合わせで JSON サイドカーで返されます。<br>ptcueformat=turner | 元素 | nfl | DPIScte35<br>pttrackingversion=v2<br>scteTracking=true<br> | HLS のみ |
| vetargetmultiplier | ライブポイントからのセグメントの数プリロールオフセットは、 ( vetargetmultiplier * targetduration ) + vebufferlength を使用して設定します。<br>注意：このパラメーターは、ライブ/リニア HLS ストリームにのみ適用されます<br>可能な値：<br>数値浮動小数点数<br>（デフォルト：3.0 - HLS 仕様と同じ） | HLS のみ |
| vebufferLength | ライブポイントからの秒数。vetargetmultiplier と組み合わせて使用します。<br>注意：このパラメーターは、ライブ/リニア HLS ストリームにのみ適用されます<br>可能な値：<br>数値浮動小数点数<br>（デフォルト：3.0） | HLS のみ |
