---
description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-title: VPAID 2.0広告のサポート
title: VPAID 2.0広告のサポート
uuid: e45e91d2-2aef-4d69-ac80-228d23e8fd7b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 概要 {#vpaid-ad-support-overview}

ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。

次の機能がサポートされています。

* VPAID仕様のバージョン2.0

   詳しくは、 [IAB VPAID 2.0を参照してください](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf)。
* ビデオオンデマンド(VOD)コンテンツを含むリニアVPAID広告
* JavaScript VPAID広告

   VPAID広告はJavaScriptベースで、広告応答はVPAID広告のメディアタイプを識別する必要があります `application/javascript`。

次の機能はサポートされていません。

* VPAID仕様のバージョン1.0
* スキップ可能な広告
* オーバーレイ広告、動的コンパニオン広告、最小化可能な広告、折りたたみ可能な広告、展開可能な広告など、ノンリニア広告。
* VPAID広告のプリロード
* ライブコンテンツのVPAID広告
* Flash VPAID広告

## API

次のAPIエレメントは、VPAID 2.0広告をサポートしています。

* のメソ `getCustomAdView` ッドは、VPAID `MediaPlayer` 広告をレ `CustomAdView` ンダリングするWebビューを表すオブジェクトを返します( [APIリファレンスを参照](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html))。

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` vpaid読み込みプロセスのタイムアウトを設定します。 デフォルトのタイムアウト値は10秒です。

VPAID広告の再生中：

* VPAID広告は、プレイヤービューの上のビューコンテナに表示されるので、プレーヤービューでのユーザーによるタップに依存するコードは機能しません。
* プレーヤーイ `pause` ンスタンス `play` に対する呼び出しと、VPAID広告の一時停止と再開。

* VPAID広告はインタラクティブになるので、VPAID広告の期間は事前に定義されていません。

   広告サーバーの応答で指定された広告の時間と合計広告の時間の時間は、正確でない場合があります。