---
description: MediaPlayer オブジェクトは、メディアプレーヤーの動作と機能をカプセル化します。
title: MediaPlayer のセットアップ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# MediaPlayer のセットアップ{#set-up-the-mediaplayer}

MediaPlayer オブジェクトは、メディアプレーヤーの動作と機能をカプセル化します。

1. のインスタンス化 `MediaPlayer` 次の方法を使用します。

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. の作成 `MediaPlayerView` インスタンス：

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   場所 `container` はターゲットです `div` 要素を `HTMLMediaElement`.

   例えば、HTMLページでは、

   ```
   <div id="videoDiv"> 
   <codeph>
     <div id="video-controls"> 
          ... custom video controls 
     </div> 
   </codeph> 
   </div>
   ```

   通話：

   ```js
   var view = new  
   <codeph>
   AdobePSDK.MediaPlayerView 
   </codeph>( 
         document.getElementById("videoDiv"));  
   ```

1. 添付する `MediaPlayerView` インスタンスを `MediaPlayer` インスタンス：

   ```js
   player.view = view;
   ```

1. カスタムコントロールのアタッチ `div` 要素を MediaPlayer インスタンスに追加します。

   例えば、HTML:

   ```
   <div id="videoDiv"> 
      <div id="video-controls"> 
         ..... custom video controls 
      </div> 
   </div>
   ```

   通話：

   ```js
   if (typeof player.getView() !== 'undefined') { 
       var view = player.view; 
       view.attachVideoControls(document.getElementById("video-controls")); 
   }
   ```

The `MediaPlayer` これで、インスタンスが使用可能になり、ビデオコンテンツをデバイス画面に表示するように適切に設定されました。
