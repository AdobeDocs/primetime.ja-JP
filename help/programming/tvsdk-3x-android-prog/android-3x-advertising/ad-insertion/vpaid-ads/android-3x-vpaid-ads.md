---
description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。
title: VPAID 2.0広告のサポート
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# 概要{#vpaid-ad-support-overview}

ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。

次の機能がサポートされています。

* VPAID仕様のバージョン2.0

   詳しくは、[IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf)を参照してください。
* ビデオオンデマンド(VOD)コンテンツを含むリニアVPAID広告
* JavaScript VPAID広告

   VPAID広告はJavaScriptベースである必要があり、広告応答はVPAID広告のメディアタイプを`application/javascript`として識別する必要があります。

次の機能はサポートされていません。

* VPAID仕様のバージョン1.0
* スキップ可能な広告
* オーバーレイ広告、動的コンパニオン広告、最小化可能な広告、折りたたみ可能な広告、展開可能な広告など、ノンリニア広告
* VPAID広告のプリロード
* ライブコンテンツ内のVPAID広告
* FlashVPAID広告

## API

以下のAPIエレメントはVPAID 2.0広告をサポートしています。

* `MediaPlayer`の`getCustomAdView`メソッドは、VPAID広告をレンダリングするWeb表示ーを表す`CustomAdView`オブジェクトを返します（[APIリファレンス](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/index.html)を参照）。

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` は、VPAID読み込みプロセスのタイムアウトを設定します。デフォルトのタイムアウト値は10秒です。

VPAID広告の再生中：

* VPAID広告は、プレイヤー表示の上の表示コンテナに表示されるので、プレイヤー表示のタップに依存するコードは機能しません。
* プレイヤーインスタンスで`pause`と`play`を呼び出すと、VPAID広告が一時停止され、再開されます。

* VPAID広告には、インタラクティブな広告が含まれる可能性があるので、広告の長さは事前に定義されたものではありません。

   広告サーバーの応答で指定される広告の継続時間と広告の時間の合計の継続時間は、正確でない場合があります。