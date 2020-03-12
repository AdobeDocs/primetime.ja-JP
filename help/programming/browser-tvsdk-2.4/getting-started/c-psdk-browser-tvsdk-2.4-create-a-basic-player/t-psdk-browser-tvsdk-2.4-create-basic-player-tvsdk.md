---
description: 次の手順を実行して、ブラウザーTVSDKを使用して基本プレーヤーを作成します。
seo-description: 次の手順を実行して、ブラウザーTVSDKを使用して基本プレーヤーを作成します。
seo-title: TVSDKを使用した基本プレーヤーの作成
title: TVSDKを使用した基本プレーヤーの作成
uuid: ec15cf53-197f-4190-a6b2-600a57815390
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# TVSDKを使用した基本プレーヤーの作成{#create-a-basic-player-using-tvsdk}

次の手順を実行して、ブラウザーTVSDKを使用して基本プレーヤーを作成します。

1. ブラウザーTVSDK用の圧縮ファイルをダウンロードできる新しいディレクトリを作成します。
1. ZendeskからブラウザーTVSDKをダウンロードし、ファイルを解凍し、frameworksフォルダーを新しいディレクトリに配置します。
1. コードの単純なHTMLボイラープレートを作成し、その中にを `div` 含めます。
1. このボイラープレートは、手順1で作成したディレクトリ内のHTMLファイルに配置します。

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

1. headセクションにブラウザーTVSDKライブラリを追加します。

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script>
   ```

1. bodyタグにセクションを追加し `onLoad` ます。

   ```
   <body onload="startVideo()">
   ```

1. 関数の実装を開始 `startVideo` します。
1. スクリプトタグを追加し、タグ内 `startVideo` に関数を作成します。

   これは、ページのheadセクションにあると想定されます。

   ```js
   <script> 
    function startVideo(){ 
    } 
   </script>
   ```

1. を作成しま `Adobe.MediaPlayer`す。

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. を作成しま `MediaPlayerView`す。

   >[!TIP]
   >
   >ここでは、前に作成し `div` たが使用されます。

   ```js
   var view = new AdobePSDK.MediaPlayerView( 
   document.getElementById("videoDiv")); 
   player.view = view;
   ```

1. プレーヤーイベントリスナーを追加します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. イベントハンドラーを実装し、追加イベントリスナーの前に配置します。

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

1. M3U8リ `MediaResource`ンク（またはmpd）を渡すを作成します。

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

1. プレイヤーがINITIALIZED状態の場合は、を呼び出しま `prepareToPlay`す。

   ```js
   case INITIALIZED: 
    player.prepareToPlay(); // <- add this line 
    break;
   ```

1. プレイヤーがPREPARED状態になったら、を呼び出しま `play`す。

   ```js
   case PREPARED: 
    player.play(); 
    break;
   ```

