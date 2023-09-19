---
description: 次の手順を実行して、Browser TVSDK を使用して基本的なプレーヤーを作成します。
title: TVSDK を使用した基本プレーヤーの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# TVSDK を使用した基本プレーヤーの作成{#create-a-basic-player-using-tvsdk}

次の手順を実行して、Browser TVSDK を使用して基本的なプレーヤーを作成します。

1. Browser TVSDK 用の圧縮ファイルをダウンロードできる新しいディレクトリを作成します。
1. Zendesk からブラウザ TVSDK をダウンロードし、ファイルを解凍し、frameworks フォルダを新しいディレクトリに配置します。
1. を使用して、コードの単純なHTMLボイラープレートを作成します。 `div` その中に
1. このボイラープレートは、手順 1 で作成したHTMLのディレクトリファイルに配置します。

   ```
   <!DOCTYPE html> 
   
   <html lang="en"> 
   <head> 
   </head> 
   <body> 
         <div id="videoDiv" width="200" height="200"> 
        <div id="video-controls"></div> 
         </div> 
   </body> 
   </html>
   ```

1. head セクションにブラウザー TVSDK ライブラリを追加します。

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script>
   ```

1. body タグに対して、 `onLoad` 」セクションに入力します。

   ```
   <body onload="startVideo()">
   ```

1. の実装を開始する `startVideo` 関数に置き換えます。
1. スクリプトタグを追加し、 `startVideo` 関数をタグ内に追加します。

   これは、ページの head セクションにあるはずです。

   ```js
   <script> 
    function startVideo(){ 
    } 
   </script>
   ```

1. を作成します。 `Adobe.MediaPlayer`.

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. を作成します。 `MediaPlayerView`.

   >[!TIP]
   >
   >ここで、 `div` 前に作成したが使用されます。

   ```js
   var view = new AdobePSDK.MediaPlayerView( 
   document.getElementById("videoDiv")); 
   player.view = view;
   ```

1. プレーヤーイベントリスナーを追加します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. イベントハンドラーを実装し、イベントリスナーの追加の前にこれを配置します。

   ```js
   var onStatusChange = function (event) { 
    console.log(event.status); 
   
    switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.IDLE: 
      console.log("Player Status: IDLE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZING: 
      console.log("Player Status: INITIALIZING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
      console.log("Player Status: INITIALIZED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARING: 
      console.log("Player Status: PREPARING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
      console.log("Player Status: PREPARED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PLAYING: 
      console.log("Player Status: PLAYING"); 
      //update UI play/pause to show pause icon 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.PAUSED: 
      console.log("Player Status: PAUSED"); 
      //update UI play/pause to show play icon & 
      //display pause icon over video 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.SEEKING: 
      console.log("Player Status: SEEKING"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.COMPLETE: 
      console.log("Player Status: COMPLETE"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: RELEASED"); 
      break; 
   
     case AdobePSDK.MediaPlayerStatus.RELEASED: 
      console.log("Player Status: ERROR"); 
      break; 
    } 
   }; 
   ```

1. を作成します。 `MediaResource`:M3U8 リンク（または mpd）を渡します。

   ```js
   var resourceUrl = "https://example.com/a/yourUrl.m3u8"; 
   var resourceType = AdobePSDK.MediaResourceType.HLS; 
   var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, null, false);
   ```

1. 空の設定を作成し、リソースを置き換えます。

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   
   player.replaceCurrentResource(mediaResource, config);
   ```

1. プレーヤーが INITIALIZED 状態になったら、を呼び出します。 `prepareToPlay`.

   ```js
   case INITIALIZED: 
    player.prepareToPlay(); // <- add this line 
    break;
   ```

1. プレーヤーが PREPARED 状態になったら、を呼び出します。 `play`.

   ```js
   case PREPARED: 
    player.play(); 
    break;
   ```
