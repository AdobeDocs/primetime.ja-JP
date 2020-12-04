---
description: TVSDKは、コンパニオンバナー広告をサポートしています。これは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
seo-description: TVSDKは、コンパニオンバナー広告をサポートしています。これは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
seo-title: コンパニオンバナー広告
title: コンパニオンバナー広告
uuid: 522578ff-1f09-48f1-91f7-f074cfd34064
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '600'
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

PTAdAssetのコンテンツは、コンパニオンバナーを記述します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

`PTMediaPlayerAdStartedNotification`通知は、`companionAssets`プロパティ（`PtAdAsset`の配列）を含む`PTAd`インスタンスを返します。
各`PtAdAsset`は、アセットの表示に関する情報を提供します。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>利用可能な情報</b></th> 
   <th colname="col2" class="entry"><b>説明</b></th> 
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
     <li id="li_76B945007CE842158B5125422765E0B2">static:データは、画像への直接的なURLであるstaticURLです。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> data </td> 
   <td colname="col2"> このコンパニオンバナーの<span class="codeph">resourceType</span>で指定されるタイプのデータです。 </td> 
  </tr> 
 </tbody> 
</table>

## バナー広告を表示{#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、TVSDKが広告関連のイベントをリッスンできるようにする必要があります。

TVSDKは、`PTMediaPlayerAdPlayStartedNotification`通知イベントを通じて、リニア広告に関連付けられたコンパニオンバナー広告のリストを提供します。

マニフェストでは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrameページのURL
* 静的な画像またはAdobeFlashのSWFファイルのURL

TVSDKは、各コンパニオン広告に対して、アプリケーションで使用できるタイプを示します。

1. ページ上の各コンパニオン広告スロットに対して`PTAdBannerView`インスタンスを作成します。

       次の情報が提供されていることを確認します。
   
   * 様々なサイズのコンパニオン広告が取得されるのを防ぐために、幅と高さを指定するバナーインスタンスを使用します。
   * 標準のバナーサイズ

1. &lt;a0追加/>の監視者で、以下を行います。`PTMediaPlayerAdStartedNotification`
   1. バナーインスタンス内の既存の広告をクリアします。
   1. `Ad.getCompanionAssets` `PTAd.companionAssets`からコンパニオン広告のリストを取得します。
   1. コンパニオン広告のリストが空でない場合、バナーインスタンスのリストを繰り返し処理します。

      各バナーインスタンス(`PTAdAsset`)には、幅、高さ、リソースタイプ（html、iframeまたは静的）などの情報、およびコンパニオンバナーの表示に必要なデータが含まれます。
   1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告に関するデータは含まれません。

      スタンドアロンディスプレイ広告を表示するには、通常のDFP（発行者はDoubleClick）ディスプレイ広告タグを適切なバナーインスタンスで実行するロジックをスクリプトに追加します。
   1. ページ上の関数にバナー情報を送信し、その関数にバナーを適切な場所に表示します。

      通常は`div`で、関数は`div ID`を使用してバナーを表示します。 例：

      ```
      - (void) onMediaPlayerAdPlayStarted:(NSNotification *) notification { 
          _currentAd  = [notification.userInfo  objectForKey:PTMediaPlayerAdKey];  
          if (_currentAd != nil) { 
              [self removeAllBanners]; // remove any existing PTAdBannerView views 
      
              // banners 
              if (_currentAd.companionAssets && _currentAd.companionAssets.count > 0) { 
                  PTAdAsset *bannerAsset = [_currentAd.companionAssets objectAtIndex:0]; 
      
                  PTAdBannerView *bannerView = [[PTAdBannerView alloc] initWithAsset:bannerAsset];  
                  bannerView.player = self.player; 
                  bannerView.delegate = self; 
      
                  bannerView.frame = CGRectMake(0.0, 0.0, bannerAsset.width, bannerAsset.height);  
                  [_adBannerView.bannerView addSubview:bannerView]; 
              } 
          } 
      }
      ```
