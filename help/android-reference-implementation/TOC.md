---
cloud: experience-cloud
product: primetime
audience: end-user
user-guide-title: Primetime Reference Implementation Help
translation-type: tm+mt
source-git-commit: abcbe6991d9a024f62554c3b5ec057f9b3c71c53

---


# Android向けPSDK 1.4リファレンスの実装 {#reference-implementation}

+ [Androidリファレンス実装の概要](home.md)
+ Primetimeリファレンスの実装 {#reference}
   + [Primetimeリファレンスの実装の使用方法](ref-implementation/how-to-use-ref-player.md)
   + [リファレンス実装構造](ref-implementation/ref-player-structure.md)
   + フィーチャマネージャの使用方法 {#feature-managers}
      + [フィーチャマネージャの使用方法](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [設定情報をMediaPlayerに渡してフィーチャマネージャを作成しています…](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [ManagerFactoryを使用した機能のオン/オフ](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [イベントの処理](ref-implementation/using-feature-managers/handling-events.md)
   + 開発環境の設定 {#setup-dev}
      + [開発環境の設定](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [前提条件ソフトウェアのダウンロードと設定](set-up-dev-environment/download-prereqs-android.md)
      + [Primetimeリファレンスの実装の構築](set-up-dev-environment/install-the-ref-player-project.md)
   + コードの調査 {#explore-code}
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [機能マネージャ](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [カタログ形式](set-up-dev-environment/exploring-code/catalog-format.md)
      + [Primetime広告のJSONオブジェクト](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [ダイレクト広告の時間のJSONオブジェクト](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [カスタム広告マーカーのJSONオブジェクト](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [エンタイトルメントリソースIDのJSONオブジェクト](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [JSONフィード形式の例](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + ビデオ再生の実装 {#implement-video}
      + [ビデオ再生の重要な操作](implement-video-playback/video-playback.md)
      + [ビデオ再生の有効化](implement-video-playback/enable-video-playback.md)
      + [DRMコンテンツの保護](implement-video-playback/content-protection.md)
   + [マルチビットレート](implement-video-playback/mbr.md)
   + 広告のあるDVR再生用のプレーヤーの設定 {#dvr}
      + [広告挿入なしのDVR](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [広告挿入付きDVR](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [DVRのカスタムスタートポイントの選択](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [参照実装でのカスタムの開始時間の設定](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [QoS再生とデバイス統計の表示](implement-video-playback/qos-statistics.md)
   + 広告の挿入 {#insert-ads}
      + [広告挿入](insert-ads/ad-insertion.md)
      + [広告挿入タイプ](insert-ads/ad-insertion-types.md)
      + [広告の追加](insert-ads/add-advertising.md)
      + [関連するAPIドキュメント](insert-ads/aps-callbacks-ad-insertion.md)
   + オーディオの遅延バインディング {#late-binding-audio}
      + [概要](late-binding-audio/late-binding-audio-overview.md)
      + [遅延バインディングオーディオの統合](late-binding-audio/aa-enable.md)
      + [オーディオトラックの選択](late-binding-audio/select-audio-tracks.md)
      + [関連するAPIドキュメント](late-binding-audio/aa-api-callbacks.md)
   + Primetime認証エンタイトルメントフロー {#primetime-authentications}
      + [概要](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Entitlement Managerの概要](paytvpass-entitlement/entitlement-overvivew.md)
      + [Primetime認証の統合](paytvpass-entitlement/integrate-pass.md)
      + [Adobe Analyticsレポートの設定](paytvpass-entitlement/pass-analytics-setup.md)
      + [関連するAPIドキュメント](paytvpass-entitlement/pass-apis-callbacks.md)
   + ビデオ分析 {#video-analytics}
      + [ビデオ分析](video-analytics/video-analytics-overview.md)
      + [ビデオ分析マネージャーの作成](video-analytics/create-video-analytics-manager.md)
      + [ビデオ分析の設定](video-analytics/configure-video-analytics-manager.md)
      + [関連するAPIドキュメント](video-analytics/va-apis-callbacks.md)
   + [カスタムユーザーインターフェイスの構築](build-custom-ui.md)
   + [トラブルシューティング](troubleshooting.md)
