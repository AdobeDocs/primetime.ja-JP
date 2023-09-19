---
description: Primetime Player Objective-C API を使用して、プレーヤーの動作をカスタマイズできます。
title: Media Player クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Media Player クラス {#media-player-classes}

Primetime Player Objective-C API を使用して、プレーヤーの動作をカスタマイズできます。

メディアプレーヤーとそのリソースを記述するクラスです。

| クラス | 説明 |
|---|---|
| PTABRControlParameters | すべての可変ビットレート制御パラメーターをカプセル化します。 次のパラメーターがサポートされています。<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | TVSDK での PTMediaPlayerClientFactory のデフォルト実装。 これは、availablePTOpportunityResolver、PTContentResolver、および PTAdPolicySelector インスタンスを提供します。 |
| PTMediaPlayer | Primetime Player フレームワークのルートコンポーネントを定義します。アプリケーションは、このクラスのインスタンスを作成してメディアを再生します。 このコンポーネントは、通知をディスパッチして、任意の時点でのプレーヤーのステータスをアプリケーションに知らせます。 |
| PTMediaPlayerClientFactory | 使用可能な PTOpportunityResolver、PTContentResolver および PTAdPolicySelector インスタンスを提供するためにカスタムメディアプレーヤークライアントファクトリが実装する必要があるメソッドを記述するプロトコル。 |
| PTMediaPlayerItem | 特定のオーディオビデオメディアを表します。 |
| PTMediaPlayerView | Primetime Player フレームワークのビューコンポーネントを管理します。 |
| PTMediaProfile | バリアントプレイリスト内の単一ストリームのプロファイルを表します。 |
| PTMediaSelectionOption | 様々な言語設定、アクセシビリティ要件またはカスタムアプリケーション設定に対応するためのオーディオビジュアルメディアリソースを表します。 有効なオプションタイプ：<ul><li>サブタイトル (PTMediaSelectionOptionTypeSubtitle)</li><li>代替オーディオ (PTMediaSelectionOptionTypeAudio)</li><li>クローズドキャプション (PTMediaSelectionOptionTypeCC)</li><li>未定義 (PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolver クラス，PTOpportunityResolver プロトコル | Adobe Primetime Ad Decisioning プロセスの配置として使用されるマニフェスト内キューの処理に使用されるクラス。 |
| PTOpportunityResolverDelegate | オポチュニティの解決の状態をデリゲートするために通信に使用するカスタムオポチュニティリゾルバー ( PTOpportunityResolver ) が使用する必要があるメソッドを記述するプロトコル。 |
| PTSDK | TVSDK のバージョンとその機能について説明します。 |
| PTSDKConfig | TVSDK のグローバル設定を公開し、アプリケーションがカスタム HLS タグをサブスクライブできるようにします。 |
| PTTextStyleRule | ルールの辞書を形成するテキストスタイル属性キーを表す定数を定義します。 |
