---
description: Android 用の MediaPlayer インターフェイスには、メディアプレーヤーの機能と動作がカプセル化されています。
title: MediaPlayer のセットアップ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# MediaPlayer のセットアップ {#set-up-the-mediaplayer}

Android 用の MediaPlayer インターフェイスには、メディアプレーヤーの機能と動作がカプセル化されています。

TVSDK は、 `MediaPlayer` インターフェイス、 `DefaultMediaPlayer` クラス。 ビデオ再生機能が必要な場合は、 `DefaultMediaPlayer`.

>[!TIP]
>
>の操作 `DefaultMediaPlayer` インスタンスのみ、 `MediaPlayer` インターフェイス。

1. パブリックを使用した MediaPlayer のインスタンス化 `DefaultMediaPlayer.create` Java Android アプリケーションコンテキストオブジェクトを渡すファクトリメソッド。

   ```java
   public static MediaPlayer create(Context context) 
   ```

1. 通話 `MediaPlayer.getView` 参照を得る `MediaPlayerView` インスタンス。

   ```java
   MediaPlayerView getView() throws IllegalStateException; 
   ```

1. を `MediaPlayerView` インスタンスの `FrameLayout` インスタンス：ビデオをデバイスの画面に配置します。

   ```java
   FrameLayout playerFrame = (FrameLayout) view.findViewById(R.id.playerFrame); 
   playerFrame.addView(mediaPlayer.getView()); 
   ```

The `MediaPlayer` これで、インスタンスが使用可能になり、ビデオコンテンツをデバイス画面に表示するように適切に設定されました。
