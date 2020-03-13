---
description: Android用のMediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。
seo-description: Android用のMediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayerの設定 {#set-up-the-mediaplayer}

Android用のMediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。

TVSDKは、インターフェイスの実装の1 `MediaPlayer` つであるクラスを提供 `DefaultMediaPlayer` します。 ビデオ再生機能が必要な場合は、インスタンスを作成しま `DefaultMediaPlayer`す。

>[!TIP]
>
>インターフェイス `DefaultMediaPlayer` で公開されているメソッドを使用してのみ、インスタンスを操作 `MediaPlayer` します。

1. パブリックファクトリメソッドを使用してMediaPlayerをイ `DefaultMediaPlayer.create` ンスタンス化し、Java Androidアプリケーションコンテキストオブジェクトを渡します。

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. を呼び `MediaPlayer.getView` 出して、インスタンスへの参照を取得 `MediaPlayerView` します。

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. インスタンス `MediaPlayerView` をインスタ `FrameLayout` ンスに配置します。インスタンスを使用すると、ビデオがデバイスの画面に配置されます。

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

これでイ `MediaPlayer` ンスタンスが使用可能になり、ビデオコンテンツをデバイスの画面に表示するように適切に設定されました。
