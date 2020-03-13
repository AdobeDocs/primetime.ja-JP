---
description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-title: VPAID 2.0広告のサポート
title: VPAID 2.0広告のサポート
uuid: 462692b5-c4b3-4488-adb3-f309809d64ad
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# VPAID 2.0広告のサポート {#vpaid-ad-support}

ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。

次の機能がサポートされています。

* VPAID仕様のバージョン2.0

   詳しくは、 [IAB VPAID 2.0を参照してください](https://www.iab.com/guidelines/digital-video-player-ad-interface-definition-vpaid-2-0/)。
* ビデオオンデマンド(VOD)コンテンツを含むリニアVPAID広告
* ライブコンテンツでは、ブラウザーTVSDKはプリロールJavaScript VPAID広告をサポートします。
* Flashフォールバックモードでは、ブラウザーTVSDKはFlashベースのVPAID広告のみをサポートします。
* リニアJavaScript VPAID広告

   VPAID広告はJavaScriptベースで、広告応答はVPAID広告のメディアタイプを識別する必要があります `application/javascript`。

次の機能はサポートされていません。

* VPAID仕様のバージョン1.0
* スキップ可能な広告
* オーバーレイ広告、動的コンパニオン広告、最小化可能な広告、折りたたみ可能な広告、展開可能な広告など、ノンリニア広告。
* VPAID広告のプリロード
* ライブコンテンツのVPAID広告
* Flash VPAID広告

## API {#section_0DB1D383CA5047B281BC808BC082C69B}

次のAPIエレメントは、VPAID 2.0広告をサポートしています。

* VPAID広 `getCustomAdView` 告をレ `MediaPlayer` ンダリング `CustomAdView` するWebビューを表すオブジェクトを返すメソッドです。

   このメソッドについて詳しくは、 `getCustomAdView` MediaPlayer APIドキュメントを [参照してください](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.MediaPlayer.html)。

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` vpaid読み込みプロセスのタイムアウトを設定します。

   デフォルトのタイムアウト値は10秒です。

* APIを使用すると、Auditude `auditudeSettings.ignoreVPAIDAds`サーバーから受信したVPAID広告を無視できます。 このAPIは、Flashフォールバックでは機能しません。

VPAID広告の再生中：

* VPAID広告は、プレイヤービューの上のビューコンテナに表示されるので、プレーヤービューでのユーザーによるタップに依存するコードは機能しません。
* プレーヤーインスタンスで一時停止および再生する呼び出し。VPAID広告を一時停止および再開します。
* VPAID広告はインタラクティブになるので、VPAID広告の期間は事前に定義されていません。

   広告サーバーの応答で指定された広告の時間と合計広告の時間の時間は、正確でない場合があります。