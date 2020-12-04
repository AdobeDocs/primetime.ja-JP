---
description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。
seo-description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。
seo-title: VPAID 2.0広告のサポート
title: VPAID 2.0広告のサポート
uuid: 462692b5-c4b3-4488-adb3-f309809d64ad
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# VPAID 2.0広告のサポート{#vpaid-ad-support}

ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。

次の機能がサポートされています。

* VPAID仕様のバージョン2.0

   詳しくは、[IAB VPAID 2.0](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/)を参照してください。
* ビデオオンデマンド(VOD)コンテンツを含むリニアVPAID広告
* ライブコンテンツでは、ブラウザーTVSDKは、プリロールJavaScript VPAID広告をサポートします。
* Flashのフォールバックモードでは、Browser TVSDKは、FlashベースのVPAID広告のみをサポートします。
* Linear JavaScript VPAID広告

   VPAID広告はJavaScriptベースである必要があり、広告応答はVPAID広告のメディアタイプを`application/javascript`として識別する必要があります。

次の機能はサポートされていません。

* VPAID仕様のバージョン1.0
* スキップ可能な広告
* オーバーレイ広告、動的なコンパニオン広告、最小化可能な広告、折りたたみ可能な広告、展開可能な広告など、ノンリニア広告。
* VPAID広告のプリロード
* ライブコンテンツ内のVPAID広告
* FlashVPAID広告

## API {#section_0DB1D383CA5047B281BC808BC082C69B}

以下のAPIエレメントはVPAID 2.0広告をサポートしています。

* `MediaPlayer`の`getCustomAdView`メソッドは、VPAID広告をレンダリングするWeb表示ーを表す`CustomAdView`オブジェクトを返します。

   `getCustomAdView`メソッドについて詳しくは、[MediaPlayer APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html)を参照してください。

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` は、VPAID読み込みプロセスのタイムアウトを設定します。

   デフォルトのタイムアウト値は10秒です。

* API `auditudeSettings.ignoreVPAIDAds`を使用すると、Auditudeサーバーから受信したVPAID広告を無視できます。 このAPIはFlashのフォールバックでは動作しません。

VPAID広告の再生中：

* VPAID広告は、プレイヤー表示の上の表示コンテナに表示されるので、プレイヤー表示でのユーザーによるタップに依存するコードは機能しません。
* プレイヤーインスタンスで一時停止および再生を呼び出して、VPAID広告を一時停止および再開します。
* VPAID広告には、インタラクティブな広告が含まれる可能性があるので、広告の長さは事前に定義されたものではありません。

   広告サーバーの応答で指定される広告の継続時間と広告の時間の合計の継続時間は、正確でない場合があります。