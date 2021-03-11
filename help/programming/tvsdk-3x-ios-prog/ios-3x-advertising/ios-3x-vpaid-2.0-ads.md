---
description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。
title: VPAID 2.0広告のサポート
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---


# VPAID 2.0広告のサポート{#vpaid-ad-support}

ビデオプレーヤー広告配信インターフェイス定義(VPAID)2.0は、ビデオ広告を再生するための共通のインターフェイスを提供します。 ユーザーにリッチメディアの操作性を提供し、発行者はターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。

次の機能がサポートされています。

* VPAID仕様のバージョン2.0

   詳しくは、[IAB VPAID 2.0](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf)を参照してください。
* ビデオオンデマンド(VOD)コンテンツのリニアVPAID広告
* JavaScript VPAID広告

   VPAID広告はJavaScriptベースである必要があり、広告応答はVPAID広告のメディアタイプを`application/javascript`として識別する必要があります。

次の機能はサポートされていません。

* VPAID仕様のバージョン1.0
* スキップ可能な広告
* オーバーレイ広告、動的コンパニオン広告、最小化可能な広告、折りたたみ可能な広告、展開可能な広告などのノンリニア広告
* VPAID広告のプリロード
* ライブコンテンツ内のVPAID広告
* FlashVPAID広告
* ポストロールVPAID広告

## APIの変更{#section_D62F3E059C6C493592D34534B0BFC150}

APIに次の変更が加えられました。

* `PTAuditudeMetadata` には、VPAID読み込みプロセスのデフォルトのタイムアウトを変更する `customAdLoadTimeout` プロパティがあります。

   デフォルトのタイムアウト値は10秒です。

* `PTMediaPlayerCustomAdNotification` が `PTMediaPlayer` インスタンスからディスパッチされる

<!--<a id="section_495700E1C5404A7B85307A4137C740C5"></a>-->

VPAID広告の再生中：

* VPAID広告は、プレイヤー表示の上の表示コンテナに表示されるので、プレイヤー表示でのユーザーによるタップに依存するコードは機能しません。
* メインコンテンツプレイヤーが一時停止し、プレイヤーインスタンスの`pause`と`play`の呼び出しを使用して、VPAID広告を一時停止および再開します。

* VPAID広告には、インタラクティブな広告が含まれる可能性があるので、広告の長さは事前に定義されたものではありません。

   広告サーバーの応答で定義される広告の継続時間と広告の時間の合計の継続時間は、正確でない場合があります。

## VPAID 2.0統合の実装{#section_63C9C737367C4A0AB4D62E0DC2084141}

iOSアプリケーションにVPAID 2.0サポートを追加するには：

1. （オプション）カスタム広告イベント追加のリスナー。

   ```
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerCustomAdNotification:) name:PTMediaPlayerCustomAdNotification object:self.player];
   ```

1. （オプション）通知を表示します。

   ```
   -(void)onMediaPlayerCustomAdNotification:(NSNotification *)notification{    PTCustomAdNotificationObject *notificationObject = [notification.userInfo objectForKey:PTCustomAdNotificationObjectKey];    if (notificationObject)    
   {        NSLog(@"ViewController:: Custom Ad Notification Received: %ld", notificationObject.type);    } 
   
   }
   ```
