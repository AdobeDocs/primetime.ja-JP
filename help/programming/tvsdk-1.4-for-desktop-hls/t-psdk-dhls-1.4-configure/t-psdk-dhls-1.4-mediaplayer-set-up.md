---
description: MediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。
title: MediaPlayerの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# MediaPlayerの設定{#set-up-the-mediaplayer}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用してプレイヤーを作成し、TVSDKのメディアプレイヤー表示に接続します。このメソッドは、ビデオの再生と管理を行うメソッドを備えています。 例えば、TVSDKは再生メソッドと一時停止メソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらのTVSDKメソッドを呼び出すボタンを設定できます。MediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。

TVSDKは、`MediaPlayer`インターフェイスを1つ実装します。DefaultMediaPlayerクラス。 ビデオ再生機能が必要な場合は、`DefaultMediaPlayer`をインスタンス化します。

>[!NOTE]
>
>`DefaultMediaPlayer`インスタンスは、`MediaPlayer`インターフェイスで公開されているメソッドでのみ操作します。

1. アプリケーションが読み込んだ`authorizedFeatures`インスタンスを使用して`MediaPlayerContext`をインスタンス化します（[署名付きトークンを読み込む](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)を参照）。

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. パブリック作成ファクトリメソッドを使用して`MediaPlayer`をインスタンス化し、`MediaPlayerContext`コンテキストオブジェクトを渡します。

   ```
   public static function create(context:Context):MediaPlayer
   ```

   これは汎用の`MediaPlayer`インターフェイスを返します。 1. `MediaPlayerView`をインスタンス化し、使用するStageVideoインスタンスを指定します。

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. `MediaPlayerView`インスタンスを新しく作成した表示に関連付けます。

   ```
   mediaPlayer.view = view;
   ```

1. `MediaPlayerView`インスタンスをデバイスの画面に配置します。

   ```
   container.addChild(view)
   ```

これで`MediaPlayer`インスタンスが使用可能になり、ビデオコンテンツがデバイス画面に表示されるように適切に設定されます。