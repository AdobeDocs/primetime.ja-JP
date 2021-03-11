---
description: MediaPlayerオブジェクトには、メディアプレイヤーの動作と機能がカプセル化されています。
title: MediaPlayerの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
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
