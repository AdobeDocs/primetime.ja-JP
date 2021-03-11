---
description: TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も提供されます。
title: メディアプレイヤーの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# メディアプレイヤーのセットアップ{#set-up-the-media-player}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も提供されます。

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

`MediaPlayer`をインスタンス化し、その表示をフレームレイアウトに配置します。

1. `MediaPlayer`をインスタンス化し、`android.content.Context`オブジェクトをコンストラクタに渡します。

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. `mediaPlayer`の`ViewGroup`を保持するフレームレイアウト(`android.widget.FrameLayout`)を提供します。

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >以下は、`_viewGroup`を作成するためのコードスニペットです。

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

   >[!NOTE]
   >
   >これで`MediaPlayer`インスタンス(`mediaPlayer`)が使用可能になり、ビデオコンテンツがデバイスの画面に表示されるように適切に設定されました。