---
description: MediaPlayerは、クリック可能な広告の再生中に広告関連のイベントをディスパッチするnotifyClick()関数を提供します。 これらのイベントは、クリックスルー機能を提供するためにアプリで使用できる広告および広告の時間の情報を提供します。
title: クリック可能な広告の処理
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# クリック可能な広告の処理{#handle-clickable-ads}

MediaPlayerは、クリック可能な広告の再生中に広告関連のイベントをディスパッチするnotifyClick()関数を提供します。 これらのイベントは、クリックスルー機能を提供するためにアプリで使用できる広告および広告の時間の情報を提供します。

MediaPlayerは、クリック可能な広告の再生時に次のイベントを実行します。

* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_CLICKED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

`AdClickedEvent`には、クリックスルー関数の処理に必要な情報が含まれています。

1. ユーザーがクリック可能な広告をクリックできるように、プレイヤーにコントロールを提供します。

   これは、ユーザーのクリックを取り込むためのボタンやその他の要素にすることができます。
1. ユーザー追加の広告クリックイベントのイベントリスナー。

   例：

   ```
   document.getElementById([ 
   <i>your_click_control_id</i>]).addEventListener("click", onAdClick);
   ```

1. ユーザー追加のclickイベントのハンドラー。

   このハンドラーは、MediaPlayerに`AdClicked`イベントを起動するように促す必要があります。

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

1. MediaPlayer広告の開始、広告がクリックされた追加、広告が完了した通知用のイベントリスナー。

   ```
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted);
   
    <i>your_player</i>().addEventListener(AdobePSDK.PSDKEventType.AD_CLICKED, onAdClickedEvent);
   ```

1. 追加イベントハンドラー。
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

   b.広告がクリックされたイベントを処理します。
この例では、イベントから広告情報を取得し、次の情報を使用して新しいブラウザーウィンドウを開きます。

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
