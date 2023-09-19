---
description: PTMediaPlayer インターフェイスは、メディアプレーヤーオブジェクトの機能と動作をカプセル化します。
title: PTMediaPlayer の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PTMediaPlayer の設定 {#set-up-the-ptmediaplayer}

TVSDK には、他の Primetime コンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetime プレーヤー）を作成するためのツールが用意されています。

プラットフォームのツールを使用して、プレーヤーを作成し、 TVSDK のメディアプレーヤービューに接続します。 TVSDK は、ビデオを再生および管理するメソッドを備えています。 例えば、 TVSDK は再生および一時停止のメソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらの TVSDK メソッドを呼び出すためのボタンを設定できます。

PTMediaPlayer インターフェイスは、メディアプレーヤーオブジェクトの機能と動作をカプセル化します。

次の手順で `PTMediaPlayer`:

1. ユーザーインターフェイスからメディアの URL を取得します。例えば、テキストフィールドなどです。

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. 作成 `PTMetadata`.

   メソッドを `createMetada` メタデータの準備 ( [広告](../ad-insertion/r-psdk-ios-1.4-advertising-requirements.md)) をクリックします。

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. 作成 `PTMediaPlayerItem` を使用して、 `PTMetadata` インスタンス。

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. TVSDK がディスパッチする通知にオブザーバーを追加します。

   ```
   [self addObservers]
   ```

1. 作成 `PTMediaPlayer` 新しい `PTMediaPlayerItem`.

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. プレーヤーにプロパティを設定します。

   次に、利用可能な `PTMediaPlayer` プロパティ：

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. プレーヤーの view プロパティを設定します。

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. 現在のビューのサブビューにプレーヤーのビューを追加します。

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. 通話 `play` メディアの再生を開始する。

   ```
   [player play];
   ```
