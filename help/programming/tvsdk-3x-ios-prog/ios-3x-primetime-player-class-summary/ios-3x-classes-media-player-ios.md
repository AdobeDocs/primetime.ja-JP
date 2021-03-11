---
description: Primetime Player Objective-C APIを使用して、プレイヤーの動作をカスタマイズできます。
title: Media Playerクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# メディアプレイヤクラス{#media-player-classes}

Primetime Player Objective-C APIを使用して、プレイヤーの動作をカスタマイズできます。

メディアプレイヤーとそのリソースを記述するクラスです。

| クラス | 説明 |
|---|---|
| PTABRControlParameters | すべての可変ビットレート制御パラメーターをカプセル化します。 次のパラメーターがサポートされています。<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | TVSDK内のPTMediaPlayerClientFactoryのデフォルト実装。 この変数は、availablePTOpportunityResolver、PTContentResolverおよびPTAdPolicySelectorの各インスタンスを提供します。 |
| PTMediaPlayer | Primetime Playerフレームワークのルートコンポーネントを定義します。アプリケーションは、このクラスのインスタンスを作成してメディアを再生します。 このコンポーネントは、通知をディスパッチして、特定の時点でのプレイヤーのステータスをアプリケーションに知らせます。 |
| PTMediaPlayerClientFactory | 使用可能なPTOpportunityResolver、PTContentResolverおよびPTAdPolicySelectorインスタンスを提供するためにカスタムメディアプレイヤークライアントファクトリが実装する必要があるメソッドを記述するプロトコル。 |
| PTMediaPlayerItem | 特定のオーディオビデオメディアを表します。 |
| PTMediaPlayerView | Primetime Playerフレームワークの表示コンポーネントを管理します。 |
| PTMediaProfile | バリアントプレイリストの単一ストリームのプロファイルを表します。 |
| PTMediaSelectionOption | 様々な言語設定、アクセシビリティ要件またはカスタムアプリケーション設定に対応するオーディオビジュアルメディアリソースを表します。 有効なオプションの種類：<ul><li>サブタイトル(PTMediaSelectionOptionTypeSubtitle)</li><li>代替オーディオ(PTMediaSelectionOptionTypeAudio)</li><li>クローズドキャプション(PTMediaSelectionOptionTypeCC)</li><li>未定義(PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolverクラス，PTOpportunityResolverプロトコル | Adobe Primetimead decisioningプロセスの場所として使用されるマニフェスト内キューを処理するために使用されるクラス。 |
| PTOpportunityResolverDelegate | オポチュニティ解決の状態を委譲するための通信でカスタムオポチュニティリゾルバー(PTOpportunityResolver)が使用する必要があるメソッドを記述するプロトコル。 |
| PTSDK | TVSDKのバージョンとその機能について説明します。 |
| PTSDKConfig | TVSDKのグローバル設定を公開し、アプリケーションがカスタムHLSタグをサブスクライブできるようにします。 |
| PTTextStyleRule | ルールの辞書を形成するテキストスタイル属性キーを表す定数を定義します。 |
