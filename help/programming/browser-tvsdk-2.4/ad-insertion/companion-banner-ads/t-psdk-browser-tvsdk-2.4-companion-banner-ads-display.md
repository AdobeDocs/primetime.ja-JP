---
description: バナー広告を表示するには、バナーインスタンスを作成し、ブラウザーTVSDKが広告関連のイベントをリッスンできるようにする必要があります。
seo-description: バナー広告を表示するには、バナーインスタンスを作成し、ブラウザーTVSDKが広告関連のイベントをリッスンできるようにする必要があります。
seo-title: バナー広告の表示
title: バナー広告の表示
uuid: aabc126e-b3aa-42dd-ab50-a7db8e324c50
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、ブラウザーTVSDKが広告関連のイベントをリッスンできるようにする必要があります。

ブラウザーTVSDKは、イベントを介してリニア広告に関連付けられたコンパニオンバナー広告のリストを提供 `AdobePSDK.PSDKEventType.AD_STARTED` します。

マニフェストでは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrameページのURL
* 静的な画像またはAdobe Flash SWFファイルのURL

ブラウザーTVSDKは、各コンパニオン広告に対して、アプリケーションで使用できるタイプを示します。

次の処理を行うイベントの `AdobePSDK.PSDKEventType.AD_STARTED` リスナーを追加します。
1. バナーインスタンス内の既存の広告をクリアします。
1. コンパニオン広告のリストを取得しま `Ad.getCompanionAssets`す。
1. コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

   各バナーインスタンス(an `AdBannerAsset`)には、幅、高さ、リソースタイプ（html、iframeまたは静的）などの情報、およびコンパニオンバナーの表示に必要なデータが含まれます。
1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。
1. バナー情報をページ上の関数に送信し、その関数によってバナーが適切な場所に表示されるようにします。

   これは通常はにな `div`り、関数ではバナーの表 `div ID` 示にを使用します。 例：

   イベントリスナーの追加：

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   リスナーハンドラーの実装：

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void 
   { 
       // check if there are any companion banner 
       if (event.ad && event.ad.companionAssets  
                    && event.ad.companionAssets.length > 0) { 
            for each (var banner:AdBannerAsset in event.ad.companionAssets) { 
               if (ExternalInterface.available) { 
                   //-- call the java script that will handle the banner display. 
                   ExternalInterface.call('addBanner', banner.resourceType,  
                       banner.width, banner.height, banner.bannerData); 
                } 
            } 
        }  
        //...        
   }
   ```

   表示を処理するJavaScriptの例：

   ```js
   function displayCompanion (resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
       var bannerDiv = document.getElementById('banner' + width + 'x' + height);  
   
       // Assuming that there is an HTML element on the page  
       // with an id of "banner300x250", for example 
       if (bannerDiv !== null) { 
           bannerDiv.innerHTML = data; 
       } 
   }
   ```

