---
description: TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も備えています。
seo-description: TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も備えています。
seo-title: メディアプレイヤーの設定
title: メディアプレイヤーの設定
uuid: 1f672484-b340-4f92-8a47-dad4c9f3b3fc
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# メディアプレイヤーの設定 {#set-up-the-media-player}

TVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。 また、ビデオ再生の品質を最大限に高めるために設計された多数の機能も備えています。

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

をインスタンス `MediaPlayer` 化し、そのビューをフレームレイアウトに配置します。

1. オブジェ `MediaPlayer`クトをコンストラクタ `android.content.Context` ーに渡して、インスタンス化します。

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. フレームレイアウト( `android.widget.FrameLayout`)を指定して、次のいずれかを `ViewGroup` 保持しま `mediaPlayer`す。

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >作成するコードスニペットを以下に示しま `_viewGroup`す。

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

   >[!NOTE]
   >
   >インスタ `MediaPlayer` ンス( `mediaPlayer`)が使用可能になり、ビデオコンテンツをデバイスの画面に表示するように適切に設定されました。