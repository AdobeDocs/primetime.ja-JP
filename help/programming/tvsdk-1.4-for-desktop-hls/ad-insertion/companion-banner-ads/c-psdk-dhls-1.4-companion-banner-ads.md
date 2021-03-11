---
description: TVSDKは、コンパニオンバナー広告をサポートしています。これは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
title: コンパニオンバナー広告
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# コンパニオンバナー広告{#companion-banner-ads}

TVSDKは、コンパニオンバナー広告をサポートしています。これは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。

コンパニオン広告を表示する際は、次の推奨事項に従ってください。

* ビデオ広告のコンパニオンバナー広告を、プレイヤーのレイアウトに収まる数だけ表示しようとします。
* 指定した高さと幅に正確に一致する場所がある場合にのみ、コンパニオンバナーを表示します。

   >[!TIP]
   >
   >バナーのサイズは変更しないでください。

* 広告開始後、できるだけ早くコンパニオンバナーを表示します。
* メインの広告/ビデオコンテナをコンパニオンバナーでオーバーレイしないでください。
* 広告の終了後も、コンパニオンバナーの表示を続けます。

   標準は、このバナーの代わりとなるまで、各コンパニオンバナーを表示することです。

## コンパニオンバナーデータ{#companion-banner-data}

AdBannerAssetのコンテンツは、コンパニオンバナーを記述します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

`AdPlaybackEvent.AD_STARTED`イベントは、`companionAssets`プロパティ(`Vector.<AdAsset>`)を含む`Ad`インスタンスを返します。
各`AdAsset`は、アセットの表示に関する情報を提供します。

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
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html:データはHTMLコードです。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe:データはiframe URL(src)です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> バナーデータ </td> 
   <td colname="col2"> このコンパニオンバナーの<span class="codeph"> resourceType</span>で指定されるタイプのデータです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的URL </td> 
   <td colname="col2"> <p>コンパニオンバナーには、画像または<span class="filepath"> .swf</span>（Flashバナー）へのダイレクトURLであるstaticURLも含まれる場合があります。 </p> <p>htmlまたはiframeを使用しない場合は、画像またはswfへのダイレクトURLを使用して、バナーをFlashステージに表示できます。 この場合、staticURLを使用してバナーを表示できます。 </p> <p>重要： 静的URLが有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用できるとは限らないからです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## バナー広告を表示{#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、TVSDKが広告関連のイベントをリッスンできるようにする必要があります。

TVSDKは、`AdPlaybackEvent.AD_STARTED`イベントイベントを介して、リニア広告に関連付けられたコンパニオンバナー広告のリストを提供します。

マニフェストでは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrameページのURL
* 静的な画像またはAdobeFlashのSWFファイルのURL

TVSDKは、各コンパニオン広告に対して、アプリケーションで使用できるタイプを示します。

&lt;a0/追加>イベントのリスナーで、次の処理を行います。`AdPlaybackEvent.AD_STARTED`

1. バナーインスタンス内の既存の広告をクリアします。

1. `Ad.companionAssets`からコンパニオン広告のリストを取得します。

1. コンパニオン広告のリストが空でない場合、バナーインスタンスのリストを繰り返し処理します。

   各バナーインスタンス(`AdBannerAsset`)には、幅、高さ、リソースタイプ（html、iframeまたは静的）などの情報、およびコンパニオンバナーの表示に必要なデータが含まれます。

1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告に関するデータは含まれません。

   スタンドアロンディスプレイ広告を表示するには、通常のDFP（発行者はDoubleClick）ディスプレイ広告タグを適切なバナーインスタンスで実行するロジックをスクリプトに追加します。

1. バナー情報をページ上の関数（通常はJavaScript）に送信し、`ExternalInterface`を使用して、バナーを適切な場所に表示します。

   通常は`div`で、関数は`div ID`を使用してバナーを表示します。 例：

   追加イベントリスナー：

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
