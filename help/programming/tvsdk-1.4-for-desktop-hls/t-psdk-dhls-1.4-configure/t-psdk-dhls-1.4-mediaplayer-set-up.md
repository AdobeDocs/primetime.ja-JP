---
description: MediaPlayerインターフェイスは、メディアプレイヤーの機能と動作をカプセル化します。
seo-description: MediaPlayerインターフェイスは、メディアプレイヤーの機能と動作をカプセル化します。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 4b27643c-9ccd-4abb-9793-475d06ee2a88
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# MediaPlayerの設定 {#set-up-the-mediaplayer}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用して、プレイヤーを作成し、TVSDKのメディアプレイヤービューに接続します。TVSDKは、ビデオの再生と管理のメソッドを備えています。 例えば、TVSDKは再生メソッドと一時停止メソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらのTVSDKメソッドを呼び出すボタンを設定できます。MediaPlayerインターフェイスは、メディアプレイヤーの機能と動作をカプセル化します。

TVSDKは、次のインターフェイスの単一の実装を提供 `MediaPlayer` します。defaultmediaplayerクラス。 ビデオ再生機能が必要な場合は、インスタンスを作成しま `DefaultMediaPlayer`す。

>[!NOTE]
>
>インターフェイスで公 `DefaultMediaPlayer` 開されているメソッドを使用してのみ、インスタンスを操作 `MediaPlayer` します。

1. アプリケーション `MediaPlayerContext` が読み込んだインスタンスを使用し `authorizedFeatures` て、インスタンスをインスタ [ンス化します(署名付きトークンの読み込みを参照](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md))。

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. パブリック作成フ `MediaPlayer` ァクトリメソッドを使用し、コンテキストオブジェクトを渡して、をインスタ `MediaPlayerContext` ンス化します。

   ```
   public static function create(context:Context):MediaPlayer
   ```

   これは汎用インターフェイスを返 `MediaPlayer` します。 1.使用するStageVideoイ `MediaPlayerView` ンスタンスをインスタンス化し、指定します。

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. 新しく作成し `MediaPlayerView` たビューにインスタンスを関連付けます。

   ```
   mediaPlayer.view = view;
   ```

1. デバイスの `MediaPlayerView` 画面にインスタンスを配置します。

   ```
   container.addChild(view)
   ```

これでイ `MediaPlayer` ンスタンスが使用可能になり、ビデオコンテンツをデバイスの画面に表示するように適切に設定されました。