---
description: TVSDK は、コンパニオンバナー広告をサポートします。コンパニオンバナー広告とは、リニア広告に付随する広告で、多くの場合、リニア広告の終了後もページ上に残ります。 アプリケーションは、リニア広告と共に提供されるコンパニオンバナーを表示する必要があります。
title: コンパニオンバナー広告
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '557'
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

PTAdAsset のコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

The `PTMediaPlayerAdStartedNotification` 通知が返す `PTAd` 次を含むインスタンス： `companionAssets` プロパティ（の配列） `PtAdAsset`) をクリックします。
各 `PtAdAsset` には、アセットの表示に関する情報が記載されています。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>利用可能な情報</b></th> 
   <th colname="col2" class="entry"><b>説明</b></th> 
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
     <li id="li_76B945007CE842158B5125422765E0B2">static：データは画像への直接 URL である staticURL です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> データ </td> 
   <td colname="col2"> で指定されるタイプのデータ <span class="codeph">resourceType</span> このコンパニオンバナー用に </td> 
  </tr> 
 </tbody> 
</table>

## バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、 TVSDK が広告関連のイベントをリッスンできるようにする必要があります。

TVSDK は、 `PTMediaPlayerAdPlayStartedNotification` 通知イベント。

マニフェストは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrame ページの URL
* 静的画像またはAdobeFlashSWFファイルの URL

TVSDK は、各コンパニオン広告に対して、アプリケーションで使用可能なタイプを示します。

1. の作成 `PTAdBannerView`  ページ上の各コンパニオン広告スロットのインスタンスです。

       次の情報が提供されていることを確認します。
   
   * 異なるサイズのコンパニオン広告が取得されるのを防ぐために、幅と高さを指定するバナーインスタンスを提供する。
   * 標準バナーサイズ。

1. 監視者を追加 `PTMediaPlayerAdStartedNotification` これは次の処理を行います。
   1. バナーインスタンス内の既存の広告をクリアします。
   1. 次のコンパニオン広告のリストを取得します： `Ad.getCompanionAssets` `PTAd.companionAssets`.
   1. コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

      各バナーインスタンス ( `PTAdAsset`) には、幅、高さ、リソースタイプ（html、iframe、静的）などの情報や、コンパニオンバナーの表示に必要なデータが含まれます。
   1. ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。

      スタンドアロンのディスプレイ広告を表示するには、スクリプトにロジックを追加して、通常の DFP(DoubleClick for Publishers) ディスプレイ広告タグを適切なバナーインスタンスで実行します。
   1. バナー情報をページ上の関数に送信し、その関数がバナーを適切な場所に表示します。

      これは通常、 `div`を検索し、関数で `div ID` バナーを表示します。 例：

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
