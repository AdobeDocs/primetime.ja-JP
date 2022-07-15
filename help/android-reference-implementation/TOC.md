---
product: primetime
audience: end-user
user-guide-title: Primetime リファレンス実装のヘルプ
user-guide-description: TVSDK を理解し、機能マネージャーを変更して、個人用プレイヤーをカスタマイズします。
source-git-commit: 95626ebde981d1996652a67bc9e0cea05f24aa6d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Android 向け PSDK 1.4 リファレンス実装 {#reference-implementation}

+ [Android リファレンス実装の概要](home.md)
+ Primetime リファレンス実装 {#reference}
   + [Primetime リファレンス実装の使用方法](ref-implementation/how-to-use-ref-player.md)
   + [参照実装構造](ref-implementation/ref-player-structure.md)
   + 機能マネージャの使用方法 {#feature-managers}
      + [機能マネージャの使用方法](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [設定情報を MediaPlayer に渡して機能マネージャーを作成しています…](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [ManagerFactory を使用した機能のオン/オフ](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [イベントの処理](ref-implementation/using-feature-managers/handling-events.md)
   + 開発環境の設定 {#setup-dev}
      + [開発環境の設定](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [前提条件のソフトウェアをダウンロードして構成](set-up-dev-environment/download-prereqs-android.md)
      + [Primetime リファレンス実装の構築](set-up-dev-environment/install-the-ref-player-project.md)
   + コードの参照 {#explore-code}
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [機能マネージャ](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [カタログ形式](set-up-dev-environment/exploring-code/catalog-format.md)
      + [Primetime 広告の JSON オブジェクト](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [直接広告ブレークの JSON オブジェクト](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [カスタム広告マーカー用の JSON オブジェクト](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [エンタイトルメントリソース ID の JSON オブジェクト](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [JSON フィード形式の例](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + ビデオ再生の実装 {#implement-video}
      + [ビデオ再生の重要な操作](implement-video-playback/video-playback.md)
      + [ビデオ再生を有効にする](implement-video-playback/enable-video-playback.md)
      + [DRM コンテンツの保護](implement-video-playback/content-protection.md)
   + [複数のビットレート](implement-video-playback/mbr.md)
   + 広告のある DVR 再生用のプレーヤーの設定 {#dvr}
      + [広告挿入のない DVR](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [広告挿入付き DVR](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [DVR のカスタム開始点の選択](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [参照実装でのカスタム開始時間の設定](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [QoS 再生とデバイス統計の表示](implement-video-playback/qos-statistics.md)
   + 広告の挿入 {#insert-ads}
      + [広告挿入](insert-ads/ad-insertion.md)
      + [広告挿入のタイプ](insert-ads/ad-insertion-types.md)
      + [広告の追加](insert-ads/add-advertising.md)
      + [関連する API ドキュメント](insert-ads/aps-callbacks-ad-insertion.md)
   + 遅延バインディングオーディオ {#late-binding-audio}
      + [概要](late-binding-audio/late-binding-audio-overview.md)
      + [遅延バインディングオーディオの統合](late-binding-audio/aa-enable.md)
      + [オーディオトラックを選択](late-binding-audio/select-audio-tracks.md)
      + [関連する API ドキュメント](late-binding-audio/aa-api-callbacks.md)
   + Primetime 認証のエンタイトルメントフロー {#primetime-authentications}
      + [概要](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Entitlement Manager の概要](paytvpass-entitlement/entitlement-overvivew.md)
      + [Primetime 認証の統合](paytvpass-entitlement/integrate-pass.md)
      + [Adobe Analytics Reporting の設定](paytvpass-entitlement/pass-analytics-setup.md)
      + [関連する API ドキュメント](paytvpass-entitlement/pass-apis-callbacks.md)
   + ビデオ分析 {#video-analytics}
      + [ビデオ分析](video-analytics/video-analytics-overview.md)
      + [ビデオ分析マネージャーの作成](video-analytics/create-video-analytics-manager.md)
      + [ビデオ分析の設定](video-analytics/configure-video-analytics-manager.md)
      + [関連する API ドキュメント](video-analytics/va-apis-callbacks.md)
   + [カスタムユーザーインターフェイスの作成](build-custom-ui.md)
   + [トラブルシューティング](troubleshooting.md)
