---
description: MediaPlayerオブジェクトには、メディアプレイヤーの動作と機能がカプセル化されています。
seo-description: MediaPlayerオブジェクトには、メディアプレイヤーの動作と機能がカプセル化されています。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 2279e388-6fbc-49a2-8560-218d3d31e1d6
translation-type: tm+mt
source-git-commit: af9b865bc1627a97bf8957b5460ff9b46052a7dc
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# MediaPlayerの設定{#set-up-the-mediaplayer}

MediaPlayerオブジェクトには、メディアプレイヤーの動作と機能がカプセル化されています。

1. 次を使用して`MediaPlayer`をインスタンス化します。

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. `MediaPlayerView`インスタンスを作成します。

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   `container`は、`HTMLMediaElement`を含むターゲット`div`です。

   例えば、HTMLページの場合：

   ```
   <div id="videoDiv"> 
   <codeph>
     <div id="video-controls"> 
          ... custom video controls 
     </div> 
   </codeph> 
   </div>
   ```

   呼び出し：

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. `MediaPlayerView`インスタンスを`MediaPlayer`インスタンスに接続します。

   ```js
   player.view = view;
   ```

1. カスタムコントロール`div`要素をMediaPlayerインスタンスにアタッチします。

   例えば、HTMLの場合：

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   呼び出し：

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

これで`MediaPlayer`インスタンスが使用可能になり、ビデオコンテンツがデバイス画面に表示されるように適切に設定されます。
