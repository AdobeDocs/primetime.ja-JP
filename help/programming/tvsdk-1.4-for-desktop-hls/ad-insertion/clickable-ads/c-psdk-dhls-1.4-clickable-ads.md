---
description: TVSDKは、クリックスルー広告に対して行動を起こすための情報を提供します。 プレイヤーのUIを作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
seo-description: TVSDKは、クリックスルー広告に対して行動を起こすための情報を提供します。 プレイヤーのUIを作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
seo-title: クリック可能な広告
title: クリック可能な広告
uuid: edefbc66-2d30-441d-9c30-256588504463
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# クリック可能な広告 {#clickable-ads}

TVSDKは、クリックスルー広告に対して行動を起こすための情報を提供します。 プレイヤーのUIを作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

TVSDK for Flash Runtimeの場合、リニア広告のみがクリック可能です。

## 広告のクリックに対する対応 {#respond-to-clicks-on-ads}

ユーザーが広告または関連するボタンをクリックすると、アプリケーションが応答します。 TVSDKは、リンク先URLに関する情報を提供します。

この例は、広告のクリックを管理する1つの方法を示しています。

1. 広告が再生されるたびに、メディアプレイヤーの上にボタンを表示します。 広告をクリックしたユーザーは、広告のURLにリダイレクトされます。 このボタンは、の一部で [!DNL ClickableAdsOverlay.xml]す。

   ```xml
      <?xml version="1.0"?> 
   <s:VGroup xmlns:fx="https://ns.adobe.com/mxml/2009"  
       xmlns:s="library://ns.adobe.com/flex/spark" percentWidth="100" horizontalAlign="center">     
           <fx:Declarations><fx:String id="text"/></fx:Declarations> 
           <s:Label text="{text}"  backgroundAlpha="0.75" backgroundColor="#DEDEDE"  
               color="#000000" paddingBottom="5" paddingRight="5" paddingLeft="5"  
               paddingTop="5"/> 
   </s:VGroup>
   ```

1. このオーバーレイをメディアプレイヤーのサンプルに含めま [!DNL psdkdemo.xml]す。

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. 広告の再生中にのみビューを表示するには、によってディスパッチされたイベントとイベ `onAdStart` ントを `onAdComplete` リッスンします。

   ```
   _player.addEventListener(AdPlaybackEvent.AD_STARTED, onAdStarted); 
   _player.addEventListener(AdPlaybackEvent.AD_COMPLETED, onAdCompleted); 
   ```

   ```
      private function onAdStarted(event:AdPlaybackEvent):void { 
       var primaryAsset:AdAsset = event.ad.primaryAsset; 
       if (primaryAsset.adClick != null) { 
           clickableAdsOverlay.visible = true;  
       } 
   } 
   private function onAdCompleted(event:AdPlaybackEvent):void { 
       clickableAdsOverlay.visible = false; 
   }
   ```

1. クリック可能な広告に対するユーザーのインタラクションを監視します。 ユーザーが広告またはボタンをタッチまたはクリックしたら、TVSDKに通知しま `notifyClick`す。

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. イベントをリッスン `AdclickEvent.AD_CLICK` します。

   広告が再生中の場合、TVSDKはイベントをディスパ `AdClickEvent.AD_CLICK` ッチし、このイベントからクリックスルーURLと関連情報を取得できます。

   ```
      _player.addEventListener(AdClickEvent.AD_CLICK, onAdClick);
   ```

1. ユーザーを広告のURLに転送する間、メディアプレイヤーを一時停止します。

   ```
   private function onAdClick(event:AdClickEvent):void { 
       _logger.info("#onAdClick Ad clicked. Target url is {0}", event.adClick.url);  
       _player.pause(); 
       var adRequest:URLRequest = new URLRequest(event.adClick.url); 
       navigateToURL(adRequest, event.adClick.title); 
   }
   ```

1. 広告のクリックスルーURLと関連情報を表示します。

       例えば、次のいずれかの方法で表示できます。
   
   * アプリケーション内のブラウザーでクリックスルーURLを開きます。

      デスクトッププラットフォームでは、通常、ビデオ広告の再生領域は、ユーザーがクリックしたときにクリックスルーURLを呼び出すために使用されます。
   * ユーザーを外部モバイルWebブラウザーにリダイレクトします。

      モバイルデバイスでは、ビデオ広告の再生領域は、コントロールの表示と非表示、再生の一時停止、フルスクリーンへの拡張など、他の機能に使用されます。 したがって、モバイルデバイスでは、通常、スポンサーボタンなどの別のビューが、クリックスルーURLを起動する手段としてユーザーに表示されます。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じ、ビデオの再生を再開します。
