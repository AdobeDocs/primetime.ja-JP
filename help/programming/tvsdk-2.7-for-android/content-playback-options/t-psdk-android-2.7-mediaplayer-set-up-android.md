---
description: MediaPlayerをインスタンス化し、そのビューをフレームレイアウトに配置します。
seo-description: MediaPlayerをインスタンス化し、そのビューをフレームレイアウトに配置します。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 49c3edb9-b6e2-49f8-b4aa-f230af7de6b0
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# MediaPlayerの設定 {#set-up-the-mediaplayer}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も備えています。

MediaPlayerをインスタンス化し、そのビューをフレームレイアウトに配置します。

1. オブジェ `MediaPlayer`クトをコンストラクタ `android.content.Context` ーに渡して、インスタンス化します。

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. フレームレイアウト( `android.widget.FrameLayout`)を指定して、次のいずれかを `ViewGroup` 保持しま `mediaPlayer`す。

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   作成するコードスニペットを以下に示しま `_viewGroup`す。

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. フレームレイアウト内にのビ `mediaPlayer` ューを配置します。

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>インスタ `MediaPlayer` ンス( `mediaPlayer`)が使用可能になり、ビデオコンテンツをデバイスの画面に表示するように適切に設定されました。