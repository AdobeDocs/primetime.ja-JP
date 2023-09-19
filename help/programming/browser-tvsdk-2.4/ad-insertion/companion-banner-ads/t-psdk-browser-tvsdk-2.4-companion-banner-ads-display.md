---
description: バナー広告を表示するには、バナーインスタンスを作成し、Browser TVSDK が広告関連のイベントをリッスンできるようにする必要があります。
title: バナー広告の表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、Browser TVSDK が広告関連のイベントをリッスンできるようにする必要があります。

ブラウザー TVSDK は、 `AdobePSDK.PSDKEventType.AD_STARTED` イベント。

マニフェストは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrame ページの URL
* 静的画像またはAdobeFlashSWFファイルの URL

各コンパニオン広告に対して、Browser TVSDK は、アプリケーションで使用可能なタイプを示します。

イベントのリスナーを追加します。 `AdobePSDK.PSDKEventType.AD_STARTED` これは次の処理を行います。
1. バナーインスタンス内の既存の広告をクリアします。
1. 次のコンパニオン広告のリストを取得します： `Ad.getCompanionAssets`.
1. コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

   各バナーインスタンス ( `AdBannerAsset`) には、幅、高さ、リソースタイプ（html、iframe、静的）などの情報や、コンパニオンバナーの表示に必要なデータが含まれます。
1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。
1. バナー情報をページ上の関数に送信し、その関数がバナーを適切な場所に表示します。

   これは通常、 `div`を検索し、関数で `div ID` バナーを表示します。 例：

   イベントリスナーを追加します。

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   リスナーハンドラーを実装します。

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

   表示を処理する JavaScript の例：

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
