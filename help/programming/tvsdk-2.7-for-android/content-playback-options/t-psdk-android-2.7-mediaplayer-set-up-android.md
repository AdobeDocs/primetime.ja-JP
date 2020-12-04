---
description: MediaPlayerをインスタンス化し、その表示をフレームレイアウトに配置します。
seo-description: MediaPlayerをインスタンス化し、その表示をフレームレイアウトに配置します。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 49c3edb9-b6e2-49f8-b4aa-f230af7de6b0
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# MediaPlayerの設定{#set-up-the-mediaplayer}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も提供されます。

MediaPlayerをインスタンス化し、その表示をフレームレイアウトに配置します。

1. `MediaPlayer`をインスタンス化し、`android.content.Context`オブジェクトをコンストラクタに渡します。

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. `mediaPlayer`の`ViewGroup`を保持するフレームレイアウト(`android.widget.FrameLayout`)を提供します。

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   以下は、`_viewGroup`を作成するためのコードスニペットです。

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. フレームレイアウト内に`mediaPlayer`の表示を配置します。

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>これで`MediaPlayer`インスタンス(`mediaPlayer`)が使用可能になり、ビデオコンテンツがデバイスの画面に表示されるように適切に設定されました。