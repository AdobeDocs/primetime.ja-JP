---
description: PTMediaPlayerインターフェイスには、メディアプレイヤーオブジェクトの機能と動作がカプセル化されています。
title: PTMediaPlayerの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# PTMediaPlayer {#set-up-the-ptmediaplayer}の設定

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用してプレイヤーを作成し、TVSDKのメディアプレイヤー表示に接続します。このメソッドは、ビデオの再生と管理を行うメソッドを備えています。 例えば、TVSDKは再生メソッドと一時停止メソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらのTVSDKメソッドを呼び出すためのボタンを設定できます。

PTMediaPlayerインターフェイスには、メディアプレイヤーオブジェクトの機能と動作がカプセル化されています。

`PTMediaPlayer`を設定するには：

1. メディアのURLをユーザインターフェイスから取得します。例えば、テキストフィールドに取得します。

   ```
   NSURL *url = [NSURL URLWithString:textFieldURL.text];
   ```

1. `PTMetadata`を作成します。

   メソッド`createMetada`がメタデータを準備するとします（[広告](../ad-insertion/r-psdk-ios-1.4-advertising-requirements.md)を参照）。

   ```
   PTMetadata *metadata = [self createMetadata]
   ```

1. `PTMetadata`インスタンスを使用して`PTMediaPlayerItem`を作成します。

   ```
   PTMediaPlayerItem *item = [[[PTMediaPlayerItem alloc] 
          initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease];
   ```

1. TVSDKがディスパッチする追加通知に対するオブザーバー。

   ```
   [self addObservers]
   ```

1. 新しい`PTMediaPlayerItem`を使用して`PTMediaPlayer`を作成します。

   ```
   PTMediaPlayer *player = [PTMediaPlayer playerWithMediaPlayerItem:item];
   ```

1. プレイヤーにプロパティを設定します。

   次に、使用可能な`PTMediaPlayer`プロパティの例を示します。

   ```
   player.autoPlay                    = YES;  
   player.closedCaptionDisplayEnabled = YES; 
   player.videoGravity                = PTMediaPlayerVideoGravityResizeAspect;  
   player.allowsAirPlayVideo          = YES;
   ```

1. プレイヤーの表示プロパティを設定します。

   ```
   CGRect playerRect = self.adPlayerView.frame;  
   playerRect.origin = CGPointMake(0, 0); 
   playerRect.size = CGSizeMake(self.adPlayerView.frame.size.width,  
                                self.adPlayerView.frame.size.height); 
   
   [player.view setFrame:playerRect]; 
   [player.view setAutoresizingMask:  
         ( UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight )];
   ```

1. 現在追加の表示のサブビュー内のプレイヤーの表示。

   ```
   [self.adPlayerView  setAutoresizesSubviews:YES];  
   [self.adPlayerView addSubview:(UIView *)player.view];
   ```

1. `play`を呼び出して開始メディアの再生を開始します。

   ```
   [player play];
   ```

