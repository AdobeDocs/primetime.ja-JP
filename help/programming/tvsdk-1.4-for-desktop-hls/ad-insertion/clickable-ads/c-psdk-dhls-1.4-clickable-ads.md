---
description: TVSDKは、クリックスルー広告に対してアクションを実行できるように情報を提供します。 プレイヤーUIを作成する際、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
title: クリック可能な広告
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# クリック可能な広告{#clickable-ads}

TVSDKは、クリックスルー広告に対してアクションを実行できるように情報を提供します。 プレイヤーUIを作成する際、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

TVSDK forFlashランタイムの場合、リニア広告のみがクリック可能です。

## 広告のクリックに反応{#respond-to-clicks-on-ads}

ユーザーが広告または関連するボタンをクリックすると、アプリケーションはレスポンスを行います。 TVSDKは、リンク先URLに関する情報を提供します。

この例は、広告のクリックを管理する1つの可能な方法を示しています。

1. 広告が再生されるたびに、メディアプレイヤーの上部にボタンを表示します。 広告をクリックするユーザーは、広告のURLにリダイレクトされます。 このボタンは[!DNL ClickableAdsOverlay.xml]の一部です。

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

1. メディアプレイヤーのサンプル[!DNL psdkdemo.xml]にこのオーバーレイを含めます。

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. 広告の再生中にのみ表示を表示するには、によってディスパッチされる`onAdStart`イベントと`onAdComplete`イベントをリッスンします。

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

1. クリック可能な広告に対するユーザーの操作を監視します。 ユーザーが広告やボタンをタッチまたはクリックしたら、`notifyClick`をTVSDKに通知します。

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. `AdclickEvent.AD_CLICK`イベントをリッスンします。

   広告の再生中に、TVSDKは`AdClickEvent.AD_CLICK`イベントをディスパッチします。この情報からクリックスルーURLと関連情報を取得できます。

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

      デスクトッププラットフォームでは、通常、ビデオ広告の再生領域は、ユーザーがクリックしたときにクリックスルーURLを呼び出すのに使用されます。
   * ユーザーを外部モバイルWebブラウザーにリダイレクトします。

      携帯端末では、ビデオ広告の再生領域は、コントロールの表示と非表示、再生の一時停止、フルスクリーンへの拡大など、他の機能に使用されます。 したがって、モバイルデバイスでは、通常、スポンサーボタンなどの別の表示が、クリックスルーURLを起動する手段としてユーザーに表示されます。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じて、ビデオの再生を再開します。
