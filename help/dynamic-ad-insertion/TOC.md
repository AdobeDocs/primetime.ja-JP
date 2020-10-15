---
cloud: experience-cloud
product: adobe primetime
audience: end-user
user-guide-title: Primetime Ad Insertion のヘルプ
user-guide-description: ユーザーをターゲットに設定した動的な広告をサーバーに挿入してコンテンツを収益化し、パーソナライズされた広告をオーディエンスに提供する方法について説明します。
translation-type: tm+mt
source-git-commit: fac84687085f289e984c189665bfe775337592b3
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 9%

---


# Primetime Ad Insertion Help {#ad-insertion}

+ [PrimetimeAd Insertionの概要](home.md)
+ PrimetimeAd Insertionの概要{#get-started}
   + [概要](get-started-ptai.md)
   + [PrimetimeAd Insertionを使用するための準備](setup-ptai.md)
   + [広告サーバーの統合](integrate-ad-server.md)
   + [CDNの統合](integrate-cdn.md)
   + [ライブ/リニアストリームでの広告挿入の使用](ad-insertion-live-linear-stream.md)
   + [VODに広告挿入を使用する](ad-insertion-vod.md)
   + [広告トラッキングの設定](set-up-ad-tracking.md)
+ [PrimetimeAd Insertionリリースノート](https://docs.adobe.com/content/help/en/primetime/release-notes/ptai/ptai-19x-release-notes.html)
+ [マニフェストサーバーデバッグツール](manifest-server-debugging-tool.md)

<!-- + [Server Side Ad Insertion debugging dashboard](ssai-debugging-dashboard.md)-->
+ Ad Insertion用マニフェストサーバーAPI {#manifest-server}
   + [マニフェストサーバーの操作の概要](msapi-topics/ms-overview.md)
   + マニフェストサーバーの概要 {#get-started}
      + [マニフェストサーバーにコマンドを送信する](msapi-topics/ms-getting-started/ms-sending-cmd.md)
      + [マニフェストサーバークエリパラメーター](msapi-topics/ms-getting-started/ms-api-query-params.md)
   + 広告挿入要求 {#ad-insert}
      + [広告挿入の要求](msapi-topics/ms-insert-ads/ms-ad-insert.md)
      + [クライアントおよび状況別のオプションのクエリパラメーター](msapi-topics/ms-insert-ads/ms-api-query-param-situation.md)
      + [フェイルオーバー/バックアップ・ストリームへのHLSプレーヤーの切り替えの促進](msapi-topics/ms-insert-ads/hls-switching-to-failover.md)
      + [マルチビットレートストリーム](msapi-topics/ms-insert-ads/ms-api-mbr-streams.md)
      + [広告の時間の部分挿入](msapi-topics/ms-insert-ads/partial-ad-break-insetion.md)
      + [CRS広告配信の複数のCDNのサポート](msapi-topics/ms-insert-ads/ms-api-multi-cdns-for-crs.md)
   + VODタイムラインの置き換え {#replace-vod}
      + [VODの変更](msapi-topics/ms-changes-vod-timeline/ms-replace-vod-timeline.md)
      + [VODタイムラインの形式](msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)
      + [VODタイムラインの置き換え](msapi-topics/ms-changes-vod-timeline/t-ms-replace-vod-timeline.md)
   + 広告効果の追跡 {#ad}
      + [広告トラッキング](msapi-topics/ms-at-effectiveness/ms-at-overview.md)
      + [クライアント側の広告トラッキングの有効化](msapi-topics/ms-at-effectiveness/ms-enable-client-side-ad-tracking.md)
      + [TVSDK以外のクライアント側トラッキングの概要](msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md)
      + [プレーヤーがマニフェストサーバーとやり取りするためのAPI](msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)
      + [EXT-X-MARKER指令](msapi-topics/ms-at-effectiveness/ms-api-playlists.md)
   + [Cookie](msapi-topics/ms-cookies.md)
   + [WebVTTキャプションのサポート](msapi-topics/ms-webvtt-captions.md)
   + ファイル形式のリスト {#list}
      + [ファイル形式](msapi-topics/ms-list-file-formats/ms-api-file-formats.md)
      + [バリアントマニフェストプレイリストを要求するURLのJSON形式](msapi-topics/ms-list-file-formats/ms-json-m3u8.md)
      + [追跡URLのJSON形式](msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md)
      + [追跡URLのVMAP形式](msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md)
   + [ビデオプレーヤーの要件](msapi-topics/ms-player-req.md)
+ Primetime Creative Repackagingサービス {#crs}
   + [CRSの概要](creative-repackaging-service/crs-overview.md)
   + [CRSの主な使用方法](creative-repackaging-service/jit-async-hls-conv.md)
   + [マルチCDNのサポート](creative-repackaging-service/multi-cdn-supportt.md)
   + [JIT再パッケージの詳細ワークフロー](creative-repackaging-service/jit-repackage.md)
   + [CRSを使用したID3時間指定メタデータタグの挿入](creative-repackaging-service/inject-id3.md)
   + [再パッケージ化API](creative-repackaging-service/api-repackage.md)
