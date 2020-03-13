---
description: 発行者は、Primetimeマニフェストサーバーのクライアント側の広告追跡ワークフローで動作するHLS準拠のビデオプレーヤーを作成できます。 ライブストリームとビデオオンデマンド(VOD)の場合のマニフェストサーバーへのインターフェイスは、少し異なります。
seo-description: 発行者は、Primetimeマニフェストサーバーのクライアント側の広告追跡ワークフローで動作するHLS準拠のビデオプレーヤーを作成できます。 ライブストリームとビデオオンデマンド(VOD)の場合のマニフェストサーバーへのインターフェイスは、少し異なります。
seo-title: TVSDK以外のクライアント側トラッキングの概要
title: TVSDK以外のクライアント側トラッキングの概要
uuid: fb23be01-3327-443d-82c4-fb0993e7fec1
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# TVSDK以外のクライアント側トラッキングの概要 {#overview-of-non-tvsdk-client-side-tracking}

発行者は、Primetimeマニフェストサーバーのクライアント側の広告追跡ワークフローで動作するHLS準拠のビデオプレーヤーを作成できます。 ライブストリームとビデオオンデマンド(VOD)の場合のマニフェストサーバーへのインターフェイスは、少し異なります。

マニフェストサーバーは、カスタムプレーヤーが以下のURLをリクエストできるAPIを提供します。これらのURLを使用して、広告追跡イベントをレポートできます。

* 広告インプレッション
* 四分位数
* 広告ポッドの進行状況
* コンテンツポッドの進行状況

マニフェストサーバーAPIは、それを使用するビデオプレーヤーが最小要件を満たしていると想定します。 詳しくは、 [ビデオプレーヤーの要件](../../msapi-topics/ms-player-req.md) （英語のみ）を参照してください。

## クライアント側の追跡ワークフロー {#section_cst_flow}

![](assets/pt_ssai_notvsdk_csat_ai-workflow.png)

1. プレイヤーは、パブリッシャーからマニフェストサーバーのURLを取得します。
1. プレイヤーは、広告挿入要件に固有のクエリパラメーターを追加し、HTTP GETリクエストを結果のブートストラップURLに送信します。 ブートストラップURLの構文は次のとおりです。

   ```
   http{s}://{manifest-server:port}/auditude/variant/{PublisherAssetID}/{urlSafeBase64({Content URL})}.m3u8?{query parameters}
   
   For example:
   https://manifest.auditude.com/auditude/variant/
   7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/aHR0cDovL3B0ZGVtb3MuY29tL3ZpZGVvcy90b3NoZHVuZW5jcnlwdGVkL2hscy90ZXN0Mi5tM3U4.m3u8?
   u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2&__sid__=docExample02
   ```

   URLには、「コマンドのマニフェストサ [ーバーへの送信」で説明されている要素が含まれます](../../msapi-topics/ms-getting-started/ms-sending-cmd.md)。

1. マニフェストサーバーは、そのプレーヤーのセッションを確立し、一意のセッションIDを生成します。 新しいバリアントM3U8プレイリストURLを作成し、JSON応答としてプレーヤーに返します。 JSONの構文は次のとおりです。

   ```
   {
    "Master-M3U8": "https://{manifest-server:port}/auditude/variant/{PublisherAssetID}/{SessionID}/
       {urlSafeBase64(content URL)}.m3u8?u={Asset ID}&z={Zone ID}&pttrackingmode=simple&pttrackingversion=v2
       &{Any other query parameters}"
   }
   
   For example:
   https://pcor3.manifest.auditude.com/auditude/variant/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3B0ZGVtb3MuY29tL3ZpZGVvcy90b3NoZHVuZW5jcnlwdGVkL2hscy90ZXN0Mi5tM3U4.3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. プレイヤーは、JSON応答のURLを使用して、マニフェストサーバーから新しいバリアントM3U8マスタープレイリストを要求します。
1. マニフェストサーバーは、次のような構文を持つストリームレベルのプレイリストURLを含む新しいバリアントM3U8を返します。

   ```
   http{s}://{manifest-server:port}/auditude/{live|vod}/{PublisherAssetID}/
     {rendition}/{groupID}/{urlSafeBase64(bit rate stream URL)}.m3u8?u={Ad Request Id}&z={Ad Zone Id}&{Any other query parameters}
   
   For example:
   #EXTM3U
   #EXT-X-VERSION:5
   #EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,DEFAULT=YES,FORCED=NO,LANGUAGE="eng",URI="https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/webvtt/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvd2VidnR0L1RPUy1lbjIubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2"
   #EXT-X-STREAM-INF:BANDWIDTH=10000000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/10000/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMTAwMDAvdG9jXzEwMDAwLm0zdTg.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=1300000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/1300/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMTMwMC90b2NfMTMwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=3400000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/3400/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMzQwMC90b2NfMzQwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=2100000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/2100/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvMjEwMC90b2NfMjEwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=800000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/800/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvODAwL3RvY184MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=5000000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/5000/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwMC90b2NfNTAwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=7500000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/7500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNzUwMC90b2NfNzUwMC5tM3U4.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   #EXT-X-STREAM-INF:BANDWIDTH=500000,SUBTITLES="subs"
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. プレイヤーは、広告が関連付けられたコンテンツを再生するために、適切なシングルビットレート、ストリームレベルのマニフェストURLを選択します。 例：

   ```
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d&z=173475&pttrackingmode=simple&pttrackingversion=v2
   ```

1. マニフェストサーバーは、コンテンツおよび広告TSセグメントリンクへのリンクを含むストリームレベルマニフェストを返します。 例：

   ```
      #EXTM3U
   #EXT-X-VERSION:3
   #EXT-X-TARGETDURATION:8
   #EXT-X-PLAYLIST-TYPE:VOD
   
   #EXT-X-DISCONTINUITY
   #EXTINF:8,
   https://primetime-a.akamaihd.net/assets/repackage/production/zen/195/10516675/2ac89785ee8df17a31b2594c61f6921e-300k-00001.ts
   #EXTINF:7,
   https://primetime-a.akamaihd.net/assets/repackage/production/zen/195/10516675/2ac89785ee8df17a31b2594c61f6921e-300k-00002.ts
   
   #EXT-X-DISCONTINUITY
   #EXTINF:4,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.0.ts
   #EXTINF:4,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.4000.ts
   #EXTINF:4.833,
   https://www.ptdemos.com/videos/toshdunencrypted/hls/500/toc_500.8000.ts   
   ```

   >[!NOTE]
   >
   >プレイヤーは、ストリームレベルのプレイリストURLを選択し、コンテンツストリームを取得する。 マニフェストサーバーは、CDNから元のプレイリストを取得します。 エンコーダによっては、title属性に次のような追加の詳 `#EXTINF` 細情報を挿入する場合があります。
   >
   >
   ```
   >#EXTINF:6.006,LTC=2017-08-23T13:25:47+00:00
   >```

   マニフェストサーバーは、広告関連付けされたプレイリストに対して非標準の属性の意味を推測して変更することができないので、マニフェストサーバーは、このタグの継続時間情報を超えるすべての追加属性を削除します。 詳しくは、 [HLS仕様の](https://tools.ietf.org/html/rfc8216#section-4.3.2.1) EXTINFエントリを参照してください。


1. 追跡情報を要求するために、プレーヤーは、選択したビットレートの `pttrackingposition` ストリームレベルのプレイリストURLに、任意の英数字の値を持つクエリパラメーターを追加します。 例：

   ```
   https://pcor3.manifest.auditude.com/auditude/vod/7LTc86_kMUDFcCjoH9X7K_2auwb_gnWM/500/f958bef8-9158-43cc-80b9-4b15417b7895/aHR0cDovL3d3dy5wdGRlbW9zLmNvbS92aWRlb3MvdG9zaGR1bmVuY3J5cHRlZC9obHMvNTAwL3RvY181MDAubTN1OA.m3u8?u=9a2893fd893cab27da24059ff034b78d
   &z=173475&pttrackingmode=simple&pttrackingversion=v2&pttrackingposition=1
   ```

1. マニフェストサーバーは、現在要求されているストリームレベルのm3u8ファイルの広告追跡データを含む [JSON](../../msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md) または [VMAP](../../msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md) オブジェクトが入力されたプレイリストファイルを返します。

   >[!NOTE]
   >
   >マニフェストサーバーは、現在要求されているストリームレベルのプレイリストに広告が挿入された場合にのみ、広告トラッキングオブジェクトを生成します。 プレーヤーが、挿入された広告を含まないプレイリストを再生している場合、マニフェストサーバーは、広告追跡プレイリスト要求に対してHTTPステータス201を返します。 プレイヤーが再生中でないストリームに対して広告トラッキングリクエストを行った場合、マニフェストサーバーはHTTPステータス500を返します。 例えば、現在の再生要求が500.m3u8用の場合、マニフェストサーバーは、広告トラッキング要求の500.m3u8内のJSON|VMAPを返します。 ただし、プレーヤーがその後ストリームを切り替えて800.m3u8を再生すると、500.m3u8の広告追跡情報が無効になり、404エラーが発生します。

   >[!NOTE]
   >
   >マニフェストサーバーは、ブートストラップURLの値に基づいて広 `pttrackingversion` 告追跡オブジェクトを生成します。 が省略された `pttrackingversion` か無効な値を持つ場合、マニフェストサーバーは、要求された各ストリームレベルプレイリストのタグ内に、 `#EXT-X-MARKER` 広告追跡情報を自動的に設定します。 詳しく [は、を参照してください](../../msapi-topics/ms-at-effectiveness/ms-api-playlists.md)。

1. プレイヤーは、各広告トラッキングイベントの各広告トラッキングURLを適切なタイミングでリクエストします。

>[!NOTE]
>
>ライブストリームの場合、パッケージャーはライブイベントの間、常にプレイリストを更新するので、プレーヤーは手順6 ～ 10を繰り返す必要があります。

ビデオの再生時に、プレーヤーは再生ヘッドの位置を追跡し、この位置を、Primetime広告挿入から受け取った追跡URLと組み合わせて使用する必要があります。 追跡URLは、再生の開始からの時間オフセット別にグループ化されます。 各時間オフセットに対して、トラッキング情報の送信先となる各広告システムのURLが存在します。 ライブビデオとビデオオンデマンドで、形式の追加の詳細が異なります。
