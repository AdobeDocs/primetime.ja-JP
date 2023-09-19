---
description: ビデオプレーヤー広告提供インターフェイス定義 (VPAID)2.0 は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、発行者は、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。
title: VPAID 2.0 広告のサポート
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# VPAID 2.0 広告のサポート {#vpaid-ad-support}

ビデオプレーヤー広告提供インターフェイス定義 (VPAID)2.0 は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、発行者は、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。

次の機能がサポートされています。

* VPAID 仕様のバージョン 2.0

  詳しくは、 [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* ビデオオンデマンド (VOD) コンテンツを使用したリニア VPAID 広告
* JavaScript VPAID 広告

  VPAID 広告は JavaScript ベースである必要があり、広告応答は VPAID 広告のメディアタイプを `application/javascript`.

次の機能はサポートされていません。

* VPAID 仕様のバージョン 1.0
* スキップ可能な広告
* オーバーレイ広告、動的なコンパニオン広告、最小化可能な広告、折りたたみ可能な広告、拡大可能な広告などのノンリニア広告。
* VPAID 広告のプリロード
* ライブコンテンツ内の VPAID 広告
* FlashVPAID 広告

## API

次の API 要素は、VPAID 2.0 広告をサポートしています。

* The `getCustomAdView` メソッド `MediaPlayer` は、 `CustomAdView` オブジェクト。VPAID 広告をレンダリングする web ビューを表します ( [API リファレンス](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)) をクリックします。

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` は、VPAID 読み込みプロセスのタイムアウトを設定します。 デフォルトのタイムアウト値は 10 秒です。

VPAID 広告の再生中：

* VPAID 広告は、プレーヤービューの上のビューコンテナに表示されるので、プレーヤービューでのユーザーによるタップに依存するコードは機能しません。
* への呼び出し `pause` および `play` プレーヤーインスタンスで VPAID 広告を一時停止して再開します。

* VPAID 広告はインタラクティブになるので、事前に定義された期間はありません。

  広告サーバーの応答で指定されている広告の時間と合計広告の時間は、正確でない可能性があります。
