---
description: TVSDKは、コンパニオンバナー広告をサポートします。これは、リニア広告を伴う広告で、多くの場合、リニア広告の終了後もページに残る広告です。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
seo-description: TVSDKは、コンパニオンバナー広告をサポートします。これは、リニア広告を伴う広告で、多くの場合、リニア広告の終了後もページに残る広告です。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
seo-title: コンパニオンバナー広告
title: コンパニオンバナー広告
uuid: 388a1683-342c-4f3b-97c8-cfcb6c5cfee1
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# コンパニオンバナー広告 {#companion-banner-ads}

TVSDKは、コンパニオンバナー広告をサポートします。これは、リニア広告を伴う広告で、多くの場合、リニア広告の終了後もページに残る広告です。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。

コンパニオン広告を表示する際は、次の推奨事項に従ってください。

* ビデオ広告のコンパニオンバナー広告を、プレイヤーのレイアウトに収まる数だけ提示します。
* 指定した高さと幅に正確に一致する場所がある場合にのみ、コンパニオンバナーを表示します。

   >[!TIP]
   >
   >バナーのサイズは変更しないでください。

* 広告の開始後、できるだけ早くコンパニオンバナーを表示します。
* メインの広告/ビデオコンテナをコンパニオンバナーと共にオーバーレイしないでください。
* 広告の終了後も、コンパニオンバナーの表示を続けます。

   標準では、このバナーの代わりとなるまで、各コンパニオンバナーが表示されます。

## コンパニオンバナーデータ {#companion-banner-data}

AdBannerAssetのコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

このイベ `AdPlaybackEvent.AD_STARTED` ントは、プ `Ad` ロパティ( `companionAssets` )を含むインス `Vector.<AdAsset>`タンスを返します。
各レポートに `AdAsset` は、アセットの表示に関する情報が表示されます。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 利用可能な情報 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> コンパニオンバナーの幅（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> コンパニオンバナーの高さ（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> リソースタイプ </td> 
   <td colname="col2">このコンパニオンバナーのリソースタイプ： 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html:データはHTMLコードで表されます。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe:データはiframe URL(src)です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> バナーデータ </td> 
   <td colname="col2"> このコンパニオンバナーのresourceTypeで指定され <span class="codeph"> るタイプ</span> のデータです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的URL </td> 
   <td colname="col2"> <p>コンパニオンバナーには、画像または <span class="filepath"> .swf</span> （Flashバナー）への直接URLであるstaticURLも含まれる場合があります。 </p> <p>htmlまたはiframeを使用しない場合は、画像またはswfへの直接URLを使用して、代わりにFlashステージにバナーを表示できます。 この場合、staticURLを使用してバナーを表示できます。 </p> <p>重要： 静的URLが有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用可能とは限らない場合があるためです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、TVSDKが広告関連のイベントをリッスンできるようにする必要があります。

TVSDKは、イベントイベントを通じてリニア広告に関連付けられたコンパニオンバナー広告のリストを `AdPlaybackEvent.AD_STARTED` 提供します。

マニフェストでは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrameページのURL
* 静的な画像またはAdobe Flash SWFファイルのURL

TVSDKは、各コンパニオン広告に対して、アプリケーションで使用できるタイプを示します。

次の処理を行うイベント `AdPlaybackEvent.AD_STARTED` のリスナーを追加します。

1. バナーインスタンス内の既存の広告をクリアします。

1. コンパニオン広告のリストを取得しま `Ad.companionAssets`す。

1. コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

   各バナーインスタンス(a `AdBannerAsset`)には、幅、高さ、リソースタイプ（html、iframeまたは静的）などの情報、およびコンパニオンバナーの表示に必要なデータが含まれます。

1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。

   スタンドアロンのディスプレイ広告を表示するには、通常のDFP（発行者の場合はDoubleClick）ディスプレイ広告タグを実行するロジックをスクリプトに追加し、適切なバナーインスタンスに追加します。

1. バナー情報をページ上の関数（通常はJavaScript）に送信します。この関数は、を使用して、バ `ExternalInterface`ナーを適切な場所に表示します。

   これは通常はにな `div`り、関数ではバナーの表 `div ID` 示にを使用します。 例：

   イベントリスナーの追加：

   ```js
   _player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted);
   ```

   リスナーハンドラーの実装：

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

   表示を処理するJavaScriptの例：

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
