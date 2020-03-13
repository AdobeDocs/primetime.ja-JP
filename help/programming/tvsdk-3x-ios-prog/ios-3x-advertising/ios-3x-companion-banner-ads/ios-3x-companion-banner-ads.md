---
description: TVSDKは、コンパニオンバナー広告をサポートします。これは、リニア広告を伴う広告で、多くの場合、リニア広告の終了後もページに残る広告です。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
seo-description: TVSDKは、コンパニオンバナー広告をサポートします。これは、リニア広告を伴う広告で、多くの場合、リニア広告の終了後もページに残る広告です。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
seo-title: コンパニオンバナー広告
title: コンパニオンバナー広告
uuid: 522578ff-1f09-48f1-91f7-f074cfd34064
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

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

PTAdAssetのコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

通知は、 `PTMediaPlayerAdStartedNotification` プロパテ `PTAd` ィ（配列）を含むイ `companionAssets` ンスタンスを返し `PtAdAsset`ます。
各レポートに `PtAdAsset` は、アセットの表示に関する情報が表示されます。

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
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html:データはHTMLコードで表されます。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe:データはiframe URL(src)です。 </li> 
     <li id="li_76B945007CE842158B5125422765E0B2">static:データは、画像への直接URLであるstaticURLです。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> データ </td> 
   <td colname="col2"> このコンパニオンバナーの <span class="codeph">resourceType</span> で指定されるタイプのデータ。 </td> 
  </tr> 
 </tbody> 
</table>

## バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、TVSDKが広告関連のイベントをリッスンできるようにする必要があります。

TVSDKは、通知イベントを通じてリニア広告に関連付けられたコンパニオンバナー広告のリストを `PTMediaPlayerAdPlayStartedNotification` 提供します。

マニフェストでは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrameページのURL
* 静的な画像またはAdobe Flash SWFファイルのURL

TVSDKは、各コンパニオン広告に対して、アプリケーションで使用できるタイプを示します。

1. ページ上の各コ `PTAdBannerView` ンパニオン広告スロットのインスタンスを作成します。

       次の情報が提供されていることを確認します。
   
   * 様々なサイズのコンパニオン広告が取得されるのを防ぐため、幅と高さを指定するバナーインスタンス。
   * 標準のバナーサイズ。

1. 次の処理を行うオブザー `PTMediaPlayerAdStartedNotification` バーを追加します。
   1. バナーインスタンス内の既存の広告をクリアします。
   1. コンパニオン広告のリストを取得しま `Ad.getCompanionAssets``PTAd.companionAssets`す。
   1. コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

      各バナーインスタンス(a `PTAdAsset`)には、幅、高さ、リソースタイプ（html、iframeまたは静的）などの情報、およびコンパニオンバナーの表示に必要なデータが含まれます。
   1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。

      スタンドアロンのディスプレイ広告を表示するには、通常のDFP（発行者の場合はDoubleClick）ディスプレイ広告タグを実行するロジックをスクリプトに追加し、適切なバナーインスタンスに追加します。
   1. バナー情報をページ上の関数に送信し、その関数によってバナーが適切な場所に表示されるようにします。

      これは通常はにな `div`り、関数ではバナーの表 `div ID` 示にを使用します。 例：

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
