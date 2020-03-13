---
description: Video Player Ad-Serving Interface Definition(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-description: Video Player Ad-Serving Interface Definition(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-title: VPAID 2.0広告のサポート
title: VPAID 2.0広告のサポート
uuid: 7168a6e4-9c5e-4d3a-8710-867cf98e4445
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# VPAID 2.0広告のサポート {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。

次の機能がサポートされています。

* VPAID仕様のバージョン2.0

   詳しくは、 [IAB VPAID 2.0を参照してください](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf)。
* ビデオオンデマンド(VOD)コンテンツのリニアVPAID広告
* JavaScript VPAID広告

   VPAID広告はJavaScriptベースで、広告応答はVPAID広告のメディアタイプを識別する必要があります `application/javascript`。

次の機能はサポートされていません。

* VPAID仕様のバージョン1.0
* スキップ可能な広告
* オーバーレイ広告、動的コンパニオン広告、最小化可能な広告、折りたたみ可能な広告、展開可能な広告など、ノンリニア広告
* VPAID広告のプリロード
* ライブコンテンツのVPAID広告
* Flash VPAID広告

## APIの変更 {#section_D62F3E059C6C493592D34534B0BFC150}

APIに対して次の変更が行われました。

* 関数が `getCustomAdView` に追加され、VPAID広告をレ `MediaPlayer` ンダリングするWebビューを返すようになりました。

   この関数によって返されるオ `CustomAdView` ブジェクトについて詳しくは、 [APIリファレンスを参照してください](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/index.html)。

* イベント `CUSTOM_AD` は、メディアプレイヤーインスタンスからディスパッチされます。

   アプリケーションは、を実装することでイベントコールバックを登録できま `CustomAdEventListener`す。

* `MediaPlayer.setCustomAdTimeout(int milliseconds)` VPAID読み込みプロセスのデフォルトのタイムアウトを変更できます。

   デフォルトのタイムアウト値は10秒です。

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

VPAID広告の再生中：

* VPAID広告は、プレイヤービューの上のビューコンテナに表示されるので、ユーザーがプレーヤービューをタップしたことに依存するコードは機能しません。
* メインコンテンツプレイヤーが一時停止し、プレイヤーイ `pause` ンスタンス `play` に対する呼び出しと呼び出しを使用して、VPAID広告を一時停止および再開します。

* VPAID広告はインタラクティブになるので、VPAID広告の期間は事前に定義されていません。

   広告サーバーの応答で定義される広告の時間と合計広告の時間の時間は、正確でない場合があります。

## VPAID 2.0統合の実装 {#implement-vpaid-integration}

VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。

VPAID 2.0サポートを追加するには：

1. カスタム広告ビューをプレーヤーインターフェイスに追加します。

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. カスタム広告イベントのリスナーを追加します。

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```
