---
description: TVSDK は、クリックスルー広告に対して行動できるように情報を提供します。 プレーヤー UI を作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
title: クリック可能な広告
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# クリック可能な広告 {#clickable-ads}

TVSDK は、クリックスルー広告に対して行動できるように情報を提供します。 プレーヤー UI を作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

TVSDK for LinearFlashランタイムの場合、クリック可能なのはリニア広告のみです。

## 広告のクリック数への応答 {#respond-to-clicks-on-ads}

ユーザーが広告や関連するボタンをクリックすると、アプリケーションは応答を行います。 TVSDK は、宛先 URL に関する情報を提供します。

この例は、広告クリック数を管理する方法の 1 つを示しています。

1. 広告が再生されるたびに、メディアプレーヤーの上にボタンを表示します。 広告をクリックしたユーザーは、広告の URL にリダイレクトされます。 このボタンは、 [!DNL ClickableAdsOverlay.xml].

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

1. このオーバーレイをメディアプレーヤーのサンプルに含めます。 [!DNL psdkdemo.xml].

   ```xml
      <psdk:ClickableAdsOverlay id="clickableAdsOverlay"  
       visible="false"   top="10" right="0" left="0"  
       text="Click here for more information"   
       click="onAdsOverlayClicked()" 
   </psdk:ClickableAdsOverlay
   ```

1. 広告の再生中にのみビューを表示するには、 `onAdStart` および `onAdComplete` によってディスパッチされるイベント。

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

1. クリック可能な広告に対するユーザーインタラクションを監視します。 ユーザーが広告やボタンをタッチまたはクリックしたら、 TVSDK に次のように通知します。 `notifyClick`.

   ```
   private function onAdsOverlayClicked():void {     
       _mediaPlayer.view.notifyClick(); 
   }
   ```

1. をリッスンします。 `AdclickEvent.AD_CLICK` イベント。

   広告が再生中の場合、 TVSDK は `AdClickEvent.AD_CLICK` イベントに含まれ、クリックスルー URL と関連情報を取得できます。

   ```
      _player.addEventListener(AdClickEvent.AD_CLICK, onAdClick);
   ```

1. ユーザーを広告の URL に誘導する際に、メディアプレーヤーを一時停止します。

   ```
   private function onAdClick(event:AdClickEvent):void { 
       _logger.info("#onAdClick Ad clicked. Target url is {0}", event.adClick.url);  
       _player.pause(); 
       var adRequest:URLRequest = new URLRequest(event.adClick.url); 
       navigateToURL(adRequest, event.adClick.title); 
   }
   ```

1. 広告のクリックスルー URL と関連情報を表示します。

       例えば、次のいずれかの方法で表示できます。
   
   * アプリケーション内のブラウザーでクリックスルー URL を開きます。

     デスクトッププラットフォームでは、通常、ビデオ広告再生領域は、ユーザーがクリックしたときにクリックスルー URL を呼び出すために使用されます。
   * ユーザーを外部のモバイル Web ブラウザーにリダイレクトします。

     モバイルデバイスでは、ビデオ広告の再生領域は、コントロールの非表示と表示、再生の一時停止、フルスクリーンへの拡張など、他の機能に使用されます。 したがって、モバイルデバイスでは、通常、スポンサーボタンなどの別のビューが、クリックスルー URL を起動する手段としてユーザーに表示されます。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じ、ビデオの再生を再開します。
