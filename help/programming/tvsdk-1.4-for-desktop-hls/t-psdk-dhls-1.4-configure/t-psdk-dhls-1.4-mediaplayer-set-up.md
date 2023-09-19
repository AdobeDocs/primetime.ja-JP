---
description: MediaPlayer インターフェイスには、メディアプレーヤーの機能と動作がカプセル化されています。
title: MediaPlayer のセットアップ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# MediaPlayer のセットアップ {#set-up-the-mediaplayer}

TVSDK には、他の Primetime コンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetime プレーヤー）を作成するためのツールが用意されています。

プラットフォームのツールを使用して、プレーヤーを作成し、 TVSDK のメディアプレーヤービューに接続します。 TVSDK は、ビデオを再生および管理するメソッドを備えています。 例えば、 TVSDK は再生および一時停止のメソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらの TVSDK メソッドを呼び出すボタンを設定できます。 MediaPlayer インターフェイスには、メディアプレーヤーの機能と動作がカプセル化されています。

TVSDK は、 `MediaPlayer` インターフェイス：DefaultMediaPlayer クラス。 ビデオ再生機能が必要な場合は、 `DefaultMediaPlayer`.

>[!NOTE]
>
>の操作 `DefaultMediaPlayer` インスタンスのみ、 `MediaPlayer` インターフェイス。

1. のインスタンス化 `MediaPlayerContext` アプリケーションで読み込まれた `authorizedFeatures` インスタンス ( [署名付きトークンを読み込む](../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/t-psdk-dhls-1.4-get-signed-token.md)) をクリックします。

   ```
   var context:MediaPlayerContext =  
       new MediaPlayerContext(authorizedFeatures)
   ```

1. のインスタンス化 `MediaPlayer` パブリックの create ファクトリメソッドを使用して、 `MediaPlayerContext` コンテキストオブジェクト：

   ```
   public static function create(context:Context):MediaPlayer
   ```

   これにより、ジェネリックが返されます `MediaPlayer` インターフェイス。 1. `MediaPlayerView` 使用する StageVideo インスタンスを指定します。

   ```
   var view:MediaPlayerView =  
       MediaPlayerView.create(stage.stageVideos[0] )
   ```

1. を関連付ける `MediaPlayerView` 新しく作成されたビューのインスタンス：

   ```
   mediaPlayer.view = view;
   ```

1. を `MediaPlayerView` デバイスの画面のインスタンス：

   ```
   container.addChild(view)
   ```

The `MediaPlayer` これで、インスタンスが使用可能になり、ビデオコンテンツをデバイス画面に表示するように適切に設定されました。
