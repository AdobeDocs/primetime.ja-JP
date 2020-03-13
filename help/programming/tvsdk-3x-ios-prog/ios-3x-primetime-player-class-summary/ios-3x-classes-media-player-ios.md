---
description: Primetime Player Objective-C APIを使用して、プレイヤーの動作をカスタマイズできます。
seo-description: Primetime Player Objective-C APIを使用して、プレイヤーの動作をカスタマイズできます。
seo-title: Media Playerクラス
title: Media Playerクラス
uuid: 705c71b6-4e5e-46b5-a59d-13df977b04f2
translation-type: tm+mt
source-git-commit: b13f2d3f083a6ca333a4edba1c8d7261f7d448ad

---


# Media Playerクラス {#media-player-classes}

Primetime Player Objective-C APIを使用して、プレイヤーの動作をカスタマイズできます。

メディアプレイヤーとそのリソースを記述するクラスです。

| クラス | 説明 |
|---|---|
| PTABRControlParameters | すべての可変ビットレート制御パラメーターをカプセル化します。 次のパラメーターがサポートされています。<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | TVSDK内のPTMediaPlayerClientFactoryのデフォルト実装。 この変数は、availablePTOpportunityResolver、PTContentResolverおよびPTAdPolicySelectorの各インスタンスを提供します。 |
| PTMediaPlayer | Primetime Playerフレームワークのルートコンポーネントを定義します。アプリケーションは、メディアを再生するために、このクラスのインスタンスを作成します。 このコンポーネントは、通知をディスパッチして、特定の時点でのプレイヤーのステータスをアプリケーションに知らせます。 |
| PTMediaPlayerClientFactory | 使用可能なPTOpportunityResolver、PTContentResolverおよびPTAdPolicySelectorインスタンスを提供するためにカスタムメディアプレイヤークライアントファクトリが実装する必要があるメソッドを記述するプロトコル。 |
| PTMediaPlayerItem | 特定のオーディオビデオメディアを表します。 |
| PTMediaPlayerView | Primetime Playerフレームワークのビューコンポーネントを管理します。 |
| PTMediaProfile | バリアントプレイリスト内の単一ストリームのプロファイルを表します。 |
| PTMediaSelectionOption | 様々な言語設定、アクセシビリティ要件またはカスタムアプリケーション設定に対応する、オーディオビジュアルメディアリソースを表します。 有効なオプションの種類：<ul><li>サブタイトル(PTMediaSelectionOptionTypeSubtitle)</li><li>代替オーディオ(PTMediaSelectionOptionTypeAudio)</li><li>クローズドキャプション(PTMediaSelectionOptionTypeCC)</li><li>未定義(PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolverクラス，PTOpportunityResolverプロトコル | Adobe Primetime ad decisioningプロセスの配置として使用されるマニフェスト内キューの処理に使用されるクラス。 |
| PTOpportunityResolverDelegate | オポチュニティ解決のステータスを委譲するために通信するためにカスタムオポチュニティリゾルバー(PTOpportunityResolver)が使用する必要があるメソッドを記述するプロトコル。 |
| PTSDK | TVSDKのバージョンとその機能について説明します。 |
| PTSDKConfig | TVSDKのグローバル設定を公開し、アプリケーションがカスタムHLSタグをサブスクライブできるようにします。 |
| PTTextStyleRule | ルールの辞書を形成するテキストスタイル属性キーを表す定数を定義します。 |
