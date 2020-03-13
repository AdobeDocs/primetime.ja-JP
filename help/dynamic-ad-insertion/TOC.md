---
cloud: experience-cloud
product: adobe primetime
audience: end-user
user-guide-title: Primetime Dynamic Ad Insertion Help
translation-type: tm+mt
source-git-commit: 9d8fa7b8deffcf0d86f0c8343b11fad042d8d4df

---


# 動的な広告挿入のヘルプ {#ad-insertion}

+ [動的な広告挿入の概要](home.md)
+ [動的な広告挿入のリリースノート](https://docs.adobe.com/content/help/en/primetime/release-notes/ptai/ptai-19x-release-notes.html)
+ [マニフェストサーバーデバッグツール](manifest-server-debugging-tool.md)
<!-- + [Server Side Ad Insertion debugging dashboard](ssai-debugging-dashboard.md)-->
+ 広告挿入用マニフェストサーバーAPI {#manifest-server}
   + [マニフェストサーバーの操作の概要](msapi-topics/ms-overview.md)
   + マニフェストサーバーの使用を開始する {#get-started}
      + [マニフェストサーバーへのコマンドの送信](msapi-topics/ms-getting-started/ms-sending-cmd.md)
      + [マニフェストサーバーのクエリパラメーター](msapi-topics/ms-getting-started/ms-api-query-params.md)
   + 広告挿入要求 {#ad-insert}
      + [広告挿入の要求](msapi-topics/ms-insert-ads/ms-ad-insert.md)
      + [クライアントおよび状況別のオプションのクエリパラメーター](msapi-topics/ms-insert-ads/ms-api-query-param-situation.md)
      + [HLSプレーヤーからフェイルオーバー/バックアップストリームへの切り替えの促進](msapi-topics/ms-insert-ads/hls-switching-to-failover.md)
      + [マルチビットレートストリーム](msapi-topics/ms-insert-ads/ms-api-mbr-streams.md)
      + [部分的な広告の時間の挿入](msapi-topics/ms-insert-ads/partial-ad-break-insetion.md)
      + [CRS広告配信の複数CDNのサポート](msapi-topics/ms-insert-ads/ms-api-multi-cdns-for-crs.md)
   + VODタイムラインの置き換え {#replace-vod}
      + [VODの変更](msapi-topics/ms-changes-vod-timeline/ms-replace-vod-timeline.md)
      + [VODタイムラインの形式](msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)
      + [VODタイムラインの置き換え](msapi-topics/ms-changes-vod-timeline/t-ms-replace-vod-timeline.md)
   + 広告効果の追跡 {#ad}
      + [広告トラッキング](msapi-topics/ms-at-effectiveness/ms-at-overview.md)
      + [クライアント側の広告追跡の有効化](msapi-topics/ms-at-effectiveness/ms-enable-client-side-ad-tracking.md)
      + [TVSDK以外のクライアント側トラッキングの概要](msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md)
      + [プレーヤーがマニフェストサーバーとやり取りするAPI](msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)
      + [EXT-X-MARKER指令](msapi-topics/ms-at-effectiveness/ms-api-playlists.md)
   + [Cookie](msapi-topics/ms-cookies.md)
   + [WebVTTキャプションのサポート](msapi-topics/ms-webvtt-captions.md)
   + ファイル形式のリスト {#list}
      + [ファイル形式](msapi-topics/ms-list-file-formats/ms-api-file-formats.md)
      + [バリアントマニフェストプレイリストを要求するURLのJSON形式](msapi-topics/ms-list-file-formats/ms-json-m3u8.md)
      + [URLの追跡用のJSON形式](msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md)
      + [追跡URLのVMAP形式](msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md)
   + [ビデオプレーヤーの要件](msapi-topics/ms-player-req.md)
+ Primetime Creative Repackagingサービス {#crs}
   + [CRSの概要](creative-repackaging-service/crs-overview.md)
   + [CRSの主な用途](creative-repackaging-service/jit-async-hls-conv.md)
   + [マルチCDNのサポート](creative-repackaging-service/multi-cdn-supportt.md)
   + [JIT再パッケージの詳細なワークフロー](creative-repackaging-service/jit-repackage.md)
   + [CRSを使用したID3時間指定メタデータタグの挿入](creative-repackaging-service/inject-id3.md)
   + [再パッケージAPI](creative-repackaging-service/api-repackage.md)
