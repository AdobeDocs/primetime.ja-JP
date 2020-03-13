---
description: PTMediaPlayerインターフェイスは、メディアプレイヤーオブジェクトの機能と動作をカプセル化します。
seo-description: PTMediaPlayerインターフェイスは、メディアプレイヤーオブジェクトの機能と動作をカプセル化します。
seo-title: PTMediaPlayerの設定
title: PTMediaPlayerの設定
uuid: 698034d3-1260-416f-83b0-6b7d058750a0
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# PTMediaPlayerの設定 {#set-up-the-ptmediaplayer}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用して、プレイヤーを作成し、TVSDKのメディアプレイヤービューに接続します。TVSDKは、ビデオの再生と管理のメソッドを備えています。 例えば、TVSDKは再生メソッドと一時停止メソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらのTVSDKメソッドを呼び出すボタンを設定できます。

PTMediaPlayerインターフェイスは、メディアプレイヤーオブジェクトの機能と動作をカプセル化します。

次の手順で設定しま `PTMediaPlayer`す。

1. メディアのURLをユーザインターフェイスから取得します。例えば、テキストフィールドに取得します。

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. 作成しま `PTMetadata`す。

   メソッドがメタデータを準 `createMetada` 備するとします( [Advertising](../../ios-3x-advertising/ios-3x-advertising-requirements.md)を参照)。

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. インスタンス `PTMediaPlayerItem` を使用して作成 `PTMetadata` します。

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. TVSDKがディスパッチする通知にオブザーバーを追加します。

   ```
   [self addObservers]
   ```

1. 新しい `PTMediaPlayer` を使用して作成しま `PTMediaPlayerItem`す。

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. プレイヤーにプロパティを設定します。

   次に、使用可能なプロパティの一部を示 `PTMediaPlayer` します。

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. プレイヤーのviewプロパティを設定します。

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. 現在のビューのサブビューにプレイヤーのビューを追加します。

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. メディア `play` 再生を開始するための呼び出し。

   ```
   [player play];
   ```
