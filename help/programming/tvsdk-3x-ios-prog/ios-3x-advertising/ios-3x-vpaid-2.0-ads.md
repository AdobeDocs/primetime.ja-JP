---
description: Video Player Ad-Serving Interface Definition(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-description: Video Player Ad-Serving Interface Definition(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化をより良く行うことができます。
seo-title: VPAID 2.0広告のサポート
title: VPAID 2.0広告のサポート
uuid: b688d244-c5ac-4832-b5c2-cb25bc80ce8b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

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
* ポストロールVPAID広告

## APIの変更 {#section_D62F3E059C6C493592D34534B0BFC150}

APIに対して次の変更が行われました。

* `PTAuditudeMetadata` には、VPAID読み込 `customAdLoadTimeout` みプロセスのデフォルトのタイムアウトを変更するプロパティがあります。

   デフォルトのタイムアウト値は10秒です。

* `PTMediaPlayerCustomAdNotification` がインスタンスからディスパッチさ `PTMediaPlayer` れる

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

VPAID広告の再生中：

* VPAID広告は、プレイヤービューの上のビューコンテナに表示されるので、ユーザーがプレーヤービューをタップしたことに依存するコードは機能しません。
* メインコンテンツプレイヤーが一時停止し、プレイヤーイ `pause` ンスタンス `play` に対する呼び出しと呼び出しを使用して、VPAID広告を一時停止および再開します。

* VPAID広告はインタラクティブになるので、VPAID広告の期間は事前に定義されていません。

   広告サーバーの応答で定義される広告の時間と合計広告の時間の時間は、正確でない場合があります。

## VPAID 2.0統合の実装 {#section_63C9C737367C4A0AB4D62E0DC2084141}

iOSアプリケーションにVPAID 2.0サポートを追加するには：

1. （オプション）カスタム広告イベントのリスナーを追加します。

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerCustomAdNotification:) name:PTMediaPlayerCustomAdNotification object:self.player];
   ```

1. （オプション）通知を表示します。

   ```
   -(void)onMediaPlayerCustomAdNotification:(NSNotification *)notification{    PTCustomAdNotificationObject *notificationObject = [notification.userInfo objectForKey:PTCustomAdNotificationObjectKey];    if (notificationObject)    
   {        NSLog(@"ViewController:: Custom Ad Notification Received: %ld", notificationObject.type);    } 
   
   }
   ```
