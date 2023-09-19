---
description: TVSDK は、コンパニオンバナー広告をサポートします。コンパニオンバナー広告とは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
title: コンパニオンバナー広告
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# コンパニオンバナー広告 {#companion-banner-ads}

TVSDK は、コンパニオンバナー広告をサポートします。コンパニオンバナー広告とは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。

コンパニオン広告を表示する場合は、次の推奨事項に従います。

* ビデオ広告のコンパニオンバナー広告の数を、プレーヤーのレイアウトに収まる数だけ表示しようとします。
* 指定した高さと幅に完全に一致する場所がある場合にのみ、コンパニオンバナーを表示します。

  >[!TIP]
  >
  >バナーのサイズを変更しないでください。

* 広告の開始後、できるだけ早くコンパニオンバナーを表示します。
* メインの広告/ビデオコンテナをコンパニオンバナーと共にオーバーレイしないでください。
* 広告が終了した後も、コンパニオンバナーを引き続き表示します。

  標準は、このバナーの代替品が来るまで、各コンパニオンバナーを表示することです。

## コンパニオンバナーデータ {#companion-banner-data}

AdBannerAsset のコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

The `AdPlaybackEvent.AD_STARTED` イベントが返す `Ad` 次を含むインスタンス： `companionAssets` プロパティ ( `Vector.<AdAsset>`) をクリックします。
各 `AdAsset` には、アセットの表示に関する情報が記載されています。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 利用可能な情報 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 幅 </td> 
   <td colname="col2"> コンパニオンバナーの幅（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 高さ </td> 
   <td colname="col2"> コンパニオンバナーの高さ（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> リソースタイプ </td> 
   <td colname="col2">このコンパニオンバナーのリソースタイプ： 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html：データはHTMLコードです。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe：データは iframe URL(src) です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> バナーデータ </td> 
   <td colname="col2"> で指定されるタイプのデータ <span class="codeph"> resourceType</span> このコンパニオンバナー用に </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的 URL </td> 
   <td colname="col2"> <p>コンパニオンバナーには、画像または <span class="filepath"> .swf</span> （Flash バナー）。 </p> <p>html や iframe を使用しない場合は、画像または swf への直接 URL を使用して、代わりにFlashステージにバナーを表示できます。 この場合、staticURL を使用してバナーを表示できます。 </p> <p>重要：静的 URL が有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用可能とは限らない場合があるからです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、 TVSDK が広告関連のイベントをリッスンできるようにする必要があります。

TVSDK は、 `AdPlaybackEvent.AD_STARTED` イベントイベントイベント。

マニフェストは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrame ページの URL
* 静的画像またはAdobeFlashSWFファイルの URL

TVSDK は、各コンパニオン広告に対して、アプリケーションで使用可能なタイプを示します。

リスナーを `AdPlaybackEvent.AD_STARTED` イベントで次の処理をおこないます。

1. バナーインスタンス内の既存の広告をクリアします。

1. 次のコンパニオン広告のリストを取得します： `Ad.companionAssets`.

1. コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

   各バナーインスタンス ( `AdBannerAsset`) には、幅、高さ、リソースタイプ（html、iframe、静的）などの情報や、コンパニオンバナーの表示に必要なデータが含まれます。

1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。

   スタンドアロンのディスプレイ広告を表示するには、スクリプトにロジックを追加して、通常の DFP(DoubleClick for Publishers) ディスプレイ広告タグを適切なバナーインスタンスで実行します。

1. バナー情報をページ上の関数に送信します ( 通常は JavaScript で、 `ExternalInterface`：バナーを適切な場所に表示します。

   これは通常、 `div`を検索し、関数で `div ID` バナーを表示します。 例：

   イベントリスナーを追加します。

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   リスナーハンドラーを実装します。

   ```js
   private function onAdStarted(event:AdPlaybackEvent):void { 
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
   function addBanner(resourceType, width, height, data) { 
       console.log(resourceType + "," +  width + "," +  height); 
   
   //Assume an html element on the page with id like 'banner300x250' 
       var bannerDiv = document.getElementById('banner' + width +  
           'x' + height);  
       if (bannerDiv != null) { 
           if (resourceType == "html") { // for html resource 
               bannerDiv.innerHTML = data; 
           } 
           else if (resourceType == "iframe") { // for iframe resource 
               bannerDiv.innerHTML = "<iframe src='" + data +  
                   "' width='100%' height='100%'></iframe>"; 
           } 
       } 
   }
   ```
