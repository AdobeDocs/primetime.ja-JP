---
description: Video Player Ad-Serving Interface Definition(VPAID)2.0 は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、発行者は、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。
title: VPAID 2.0 広告のサポート
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# VPAID 2.0 広告のサポート {#vpaid-ad-support}

Video Player Ad-Serving Interface Definition(VPAID)2.0 は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアエクスペリエンスを提供し、発行者は、広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。

次の機能がサポートされています。

* VPAID 仕様のバージョン 2.0

  詳しくは、 [IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf).
* ビデオオンデマンド (VOD) コンテンツのリニア VPAID 広告
* JavaScript VPAID 広告

  VPAID 広告は JavaScript ベースである必要があり、広告応答は VPAID 広告のメディアタイプを `application/javascript`.

次の機能はサポートされていません。

* VPAID 仕様のバージョン 1.0
* スキップ可能な広告
* オーバーレイ広告、動的なコンパニオン広告、最小化可能な広告、折りたたみ可能な広告、拡大可能な広告などのノンリニア広告
* VPAID 広告のプリロード
* ライブコンテンツ内の VPAID 広告
* FlashVPAID 広告
* ポストロール VPAID 広告

## API の変更点 {#section_D62F3E059C6C493592D34534B0BFC150}

API に対して次の変更が加えられました。

* `PTAuditudeMetadata` には、 `customAdLoadTimeout` プロパティを使用して、VPAID 読み込みプロセスのデフォルトのタイムアウトを変更します。

  デフォルトのタイムアウト値は 10 秒です。

* `PTMediaPlayerCustomAdNotification` が `PTMediaPlayer` インスタンス

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

VPAID 広告の再生中：

* VPAID 広告は、プレーヤービューの上のビューコンテナに表示されるので、プレーヤービューでユーザーがタップしたことを使用するコードは機能しません。
* メインコンテンツプレーヤーが一時停止し、 `pause` および `play` を使用して、VPAID 広告を一時停止および再開します。

* VPAID 広告はインタラクティブになるので、事前に定義された期間はありません。

  広告サーバーの応答で定義される広告の時間と合計広告の時間は、正確でない可能性があります。

## VPAID 2.0 統合の実装 {#section_63C9C737367C4A0AB4D62E0DC2084141}

VPAID 2.0 サポートをiOSアプリケーションに追加するには：

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
