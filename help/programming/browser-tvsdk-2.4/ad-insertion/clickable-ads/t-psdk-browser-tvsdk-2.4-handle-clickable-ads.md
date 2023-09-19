---
description: MediaPlayer は、クリック可能な広告の再生中に広告関連のイベントをディスパッチする notifyClick() 関数を提供します。 これらのイベントは、アプリがクリックスルー機能を提供するために使用できる広告および広告ブレーク情報を提供します。
title: クリック可能な広告の処理
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# クリック可能な広告の処理 {#handle-clickable-ads}

MediaPlayer は、クリック可能な広告の再生中に広告関連のイベントをディスパッチする notifyClick() 関数を提供します。 これらのイベントは、アプリがクリックスルー機能を提供するために使用できる広告および広告ブレーク情報を提供します。

MediaPlayer は、クリック可能な広告が再生されると、次のイベントを発生させます。

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

The `AdClickedEvent` には、クリックスルー関数の処理に必要な情報が含まれています。

1. ユーザーがクリック可能な広告をクリックできるように、プレーヤーにコントロールを指定します。

   これには、ユーザーのクリックをキャプチャするためのボタンやその他の要素を使用できます。
1. ユーザーの広告クリックイベント用のイベントリスナーを追加します。

   例：

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. ユーザーの click イベントにハンドラーを追加します。

   このハンドラーは、MediaPlayer に対して、 `AdClicked` イベント。

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

1. MediaPlayer 広告開始、広告クリックおよび広告完了の通知用のイベントリスナーを追加します。

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. イベントハンドラーを追加します。
a.広告開始イベントを処理します。
これにより、ユーザーの UI の設定など、何らかの操作が可能になります。

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

   b.広告のクリックイベントを処理します。
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

   c.広告が完了したイベントを処理します。

   ```
   onAdCompleted = function (event) { 
       if (clickAddButton) { 
           clickAddButton.setAttribute('hidden', 'true'); 
       } 
   }
   ```
