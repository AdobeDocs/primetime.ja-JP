---
description: 次の手順を実行して、ブラウザーTVSDKを使用して基本プレーヤーを作成します。
title: TVSDKを使用した基本プレイヤーの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# TVSDK{#create-a-basic-player-using-tvsdk}を使用した基本プレイヤーの作成

次の手順を実行して、ブラウザーTVSDKを使用して基本プレーヤーを作成します。

1. ブラウザーTVSDK用の圧縮ファイルをダウンロードできる新しいディレクトリを作成します。
1. ZendeskからブラウザーTVSDKをダウンロードし、ファイルを解凍して、新しいディレクトリにframeworksフォルダーを配置します。
1. `div`を含むコード用の単純なHTMLボイラープレートを作成します。
1. このボイラープレートは、手順1で作成したディレクトリのHTMLファイルに配置します。

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

1. head追加セクションのブラウザーTVSDKライブラリ。

   ```js
   <script src= "frameworks/player/dash.min.js"></script> 
   <script src= "frameworks/player/primetimemain.min.js"></script> 
   <script src= "frameworks/player/swfobject.js"></script> 
   <script src= "frameworks/player/primetimeei.min.js"></script>
   ```

1. bodyタグに対して、`onLoad`セクションを追加します。

   ```
   <body onload="startVideo()">
   ```

1. `startVideo`関数を実装する開始です。
1. 追加スクリプトタグを作成し、タグ内に`startVideo`関数を作成します。

   これは、ページのheadセクションにあると想定されます。

   ```js
   <script> 
    function startVideo(){ 
    } 
   </script>
   ```

1. `Adobe.MediaPlayer`を作成します。

   ```js
   var player = new AdobePSDK.MediaPlayer();
   ```

1. `MediaPlayerView`を作成します。

   >[!TIP]
   >
   >ここで、先ほど作成した`div`が使用されます。

   ```js
   var view = new AdobePSDK.MediaPlayerView( 
   document.getElementById("videoDiv")); 
   player.view = view;
   ```

1. プレ追加イヤーイベントリスナー。

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

1. M3U8リンク（またはmpd）を渡す`MediaResource`を作成します。

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

1. プレイヤーがINITIALIZED状態になったら、`prepareToPlay`を呼び出します。

   ```js
   case INITIALIZED: 
    player.prepareToPlay(); // <- add this line 
    break;
   ```

1. プレイヤーがPREPARED状態になったら、`play`を呼び出します。

   ```js
   case PREPARED: 
    player.play(); 
    break;
   ```

