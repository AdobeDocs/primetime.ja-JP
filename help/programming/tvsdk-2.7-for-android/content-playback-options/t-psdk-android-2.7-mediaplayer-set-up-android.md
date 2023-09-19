---
description: MediaPlayer をインスタンス化し、そのビューをフレームレイアウトに配置します。
title: MediaPlayer のセットアップ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# MediaPlayer のセットアップ {#set-up-the-mediaplayer}

TVSDK には、他の Primetime コンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetime プレーヤー）を作成するためのツールが用意されています。 また、ビデオの再生品質を最大限に高めるために設計された多数の機能も提供します。

MediaPlayer をインスタンス化し、そのビューをフレームレイアウトに配置します。

1. インスタンス化 `MediaPlayer`，を渡す `android.content.Context` オブジェクトを次のコンストラクタに渡します。

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. フレームレイアウトを指定します ( `android.widget.FrameLayout`) を保持する `ViewGroup` / `mediaPlayer`:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   次に、作成するコードスニペットを示します。 `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. ビューを配置する `mediaPlayer` フレームレイアウト内：

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>The `MediaPlayer` インスタンス ( `mediaPlayer`) が使用可能になり、ビデオコンテンツをデバイス画面に表示するように適切に設定されました。
