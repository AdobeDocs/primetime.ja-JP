---
description: MediaPlayerは、クリック可能な広告の再生中に広告関連のイベントをディスパッチするnotifyClick()関数を提供します。 これらのイベントは、広告および広告の時間の情報を提供します。この情報は、アプリがクリックスルー機能を提供するために使用できます。
seo-description: MediaPlayerは、クリック可能な広告の再生中に広告関連のイベントをディスパッチするnotifyClick()関数を提供します。 これらのイベントは、広告および広告の時間の情報を提供します。この情報は、アプリがクリックスルー機能を提供するために使用できます。
seo-title: クリック可能な広告の処理
title: クリック可能な広告の処理
uuid: 5d3c9d36-60d7-4272-a523-7d1fe0e1615f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# クリック可能な広告の処理 {#handle-clickable-ads}

MediaPlayerは、クリック可能な広告の再生中に広告関連のイベントをディスパッチするnotifyClick()関数を提供します。 これらのイベントは、広告および広告の時間の情報を提供します。この情報は、アプリがクリックスルー機能を提供するために使用できます。

MediaPlayerは、クリック可能な広告の再生時に次のイベントを発生させます。

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

には、ク `AdClickedEvent` リックスルー関数の処理に必要な情報が含まれています。

1. ユーザーがクリック可能な広告をクリックできるように、プレイヤーにコントロールを提供します。

   これは、ユーザーのクリックをキャプチャするボタンやその他の要素にすることができます。
1. ユーザーの広告クリックイベントのイベントリスナーを追加します。

   例：

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. ユーザーのclickイベントのハンドラーを追加します。

   このハンドラーは、MediaPlayerにイベントの発生を促すプロンプトを表示する必要が `AdClicked` あります。

   ```
   onAdClick = function (event) { 
       // Get a reference to your player 
       var player = getPlayer(); 
       if (player) { 
           // Call the MediaPlayer's notifyClick function 
           // which gets MediaPlayer to fire AdClicked 
           player.notifyClick(); 
       } 
   } 
   ```

1. MediaPlayer広告開始、広告クリックおよび広告完了通知用のイベントリスナーを追加します。

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. イベントハンドラーを追加します。
a.広告開始イベントを処理します。
これは、ユーザーのUIの設定など、何でもできます。

   ```
   onAdStarted = function (event) { 
       if (clickAddButton && event && event.ad) { 
           var adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           if (adClick && adClick.isValid) { 
               // Do some initial processing  
               // when the ad starts, prior 
               // to the user's click. 
           } 
       } 
   }
   ```

   b.広告クリックイベントを処理します。
この例では、イベントから広告情報を取得し、その情報を使用して新しいブラウザーウィンドウを開きます。

   ```
   onAdClickedEvent = function (event) { 
       if (event && event.ad) { 
           var adClick = event.adClick; 
           if (!(adClick && adClick.isValid)) { 
               adClick = event.ad.primaryAsset && event.ad.primaryAsset.adClick; 
           } 
           if (adClick && adClick.isValid) 
           { 
               // Do something with the currently playing ad 
               window.open(adClick.url); 
           } 
       } 
   }
   ```

   c.広告完了イベントを処理します。

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
