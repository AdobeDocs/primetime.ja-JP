---
description: バナー広告を表示するには、バナーインスタンスを作成し、ブラウザーTVSDKが広告関連のイベントをリッスンできるようにする必要があります。
title: バナー広告を表示する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# バナー広告を表示{#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、ブラウザーTVSDKが広告関連のイベントをリッスンできるようにする必要があります。

ブラウザーTVSDKは、`AdobePSDK.PSDKEventType.AD_STARTED`イベントを介してリニア広告に関連付けられたコンパニオンバナー広告のリストを提供します。

マニフェストでは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrameページのURL
* 静的な画像またはAdobeFlashのSWFファイルのURL

各コンパニオン広告に対して、Browser TVSDKは、アプリケーションで使用できるタイプを示します。

次追加の処理を行うイベント`AdobePSDK.PSDKEventType.AD_STARTED`のリスナーです。
1. バナーインスタンス内の既存の広告をクリアします。
1. `Ad.getCompanionAssets`からコンパニオン広告のリストを取得します。
1. コンパニオン広告のリストが空でない場合、バナーインスタンスのリストを繰り返し処理します。

   各バナーインスタンス(`AdBannerAsset`)には、幅、高さ、リソースタイプ（html、iframeまたは静的）などの情報、およびコンパニオンバナーの表示に必要なデータが含まれます。
1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告に関するデータは含まれません。
1. ページ上の関数にバナー情報を送信し、その関数にバナーを適切な場所に表示します。

   通常は`div`で、関数は`div ID`を使用してバナーを表示します。 例：

   追加イベントリスナー：

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

