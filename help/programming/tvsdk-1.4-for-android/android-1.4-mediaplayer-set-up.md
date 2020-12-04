---
description: Android用のMediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。
seo-description: Android用のMediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 492b4693-acdf-4213-98e5-d6f0f1ae086d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# MediaPlayerの設定{#set-up-the-mediaplayer}

Android用のMediaPlayerインターフェイスには、メディアプレイヤーの機能と動作がカプセル化されています。

TVSDKは、`MediaPlayer`インターフェイスの実装を1つ提供します（`DefaultMediaPlayer`クラス）。 ビデオ再生機能が必要な場合は、`DefaultMediaPlayer`をインスタンス化します。

>[!TIP]
>
>`DefaultMediaPlayer`インスタンスは、`MediaPlayer`インターフェイスで公開されるメソッドでのみ操作します。

1. パブリック`DefaultMediaPlayer.create`ファクトリメソッドを使用して、Java Androidアプリケーションコンテキストオブジェクトを渡して、MediaPlayerをインスタンス化します。

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. `MediaPlayer.getView`を呼び出して、`MediaPlayerView`インスタンスへの参照を取得します。

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. `MediaPlayerView`インスタンスを`FrameLayout`インスタンスに配置します。このインスタンスにより、ビデオがデバイスの画面に配置されます。

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

これで`MediaPlayer`インスタンスが使用可能になり、ビデオコンテンツがデバイス画面に表示されるように適切に設定されます。
