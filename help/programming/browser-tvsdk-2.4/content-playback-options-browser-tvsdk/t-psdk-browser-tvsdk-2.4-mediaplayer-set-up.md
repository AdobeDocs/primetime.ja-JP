---
description: MediaPlayerオブジェクトは、メディアプレイヤーの動作と機能をカプセル化します。
seo-description: MediaPlayerオブジェクトは、メディアプレイヤーの動作と機能をカプセル化します。
seo-title: MediaPlayerの設定
title: MediaPlayerの設定
uuid: 2279e388-6fbc-49a2-8560-218d3d31e1d6
translation-type: tm+mt
source-git-commit: af9b865bc1627a97bf8957b5460ff9b46052a7dc

---


# MediaPlayerの設定{#set-up-the-mediaplayer}

MediaPlayerオブジェクトは、メディアプレイヤーの動作と機能をカプセル化します。

1. 次を使用して、を `MediaPlayer` インスタンス化します。

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. インスタンスの `MediaPlayerView` 作成：

   ```js
   var view = new AdobePSDK.MediaPlayerView(container);
   ```

   ここで、 `container` はユーザーを含む `div` ターゲット要素を示しま `HTMLMediaElement`す。

   例えば、HTMLページの場合は、次のようになります。

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

1. インスタンス `MediaPlayerView` をインスタンスにアタッチ `MediaPlayer` します。

   ```js
   player.view = view;
   ```

1. カスタムコントロール要素をMediaPlayer `div` インスタンスにアタッチします。

   例えば、HTMLの場合：

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

これでイ `MediaPlayer` ンスタンスが使用可能になり、ビデオコンテンツをデバイスの画面に表示するように適切に設定されました。
