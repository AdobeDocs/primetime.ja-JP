---
description: ユーザーが広告または関連するボタンをクリックした場合、アプリは応答する必要があります。 TVSDKは、クリックのリンク先URLに関する情報を提供します。
seo-description: ユーザーが広告または関連するボタンをクリックした場合、アプリは応答する必要があります。 TVSDKは、クリックのリンク先URLに関する情報を提供します。
seo-title: 広告のクリックに対する対応
title: 広告のクリックに対する対応
uuid: 31852f01-c900-48e3-ae23-7fb131c22594
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告のクリックに対する対応{#respond-to-clicks-on-ads}

ユーザーが広告または関連するボタンをクリックした場合、アプリは応答する必要があります。 TVSDKは、クリックのリンク先URLに関する情報を提供します。

1. TVSDKのイベントリスナーを設定し、クリックスルー情報を提供するには、を登録しま `AdClickedEventListener.onAdClicked`す。

   ユーザーが広告または関連するボタンをクリックすると、TVSDKは、クリックの宛先に関する情報を含む、この通知をディスパッチします。
1. クリック可能な広告に対するユーザーのインタラクションを監視します。
1. ユーザーが広告またはボタンをタッチまたはクリックしたときに、TVSDKに通知するには、を呼 `notifyClick` び出しま `MediaPlayerView`す。
1. TVSDKからイベント `onAdClick(AdClickEvent event)` をリッスンします。
1. クリックスルーURLと関連情報を取得するには、インスタンスのgetterメソッドを使用 `AdClickEvent` します。
1. ビデオを一時停止します。

   ビデオの一時停止について詳しくは、再生の一時停止 [と再開を参照してください](../../ad-insertion/clickable-ads/android-1.4-pausing-resuming-playback.md)。
1. クリックスルー情報を使用して、広告のクリックスルーURLと関連情報を表示します。

       例えば、次のいずれかの方法で情報を表示できます。
   
   * アプリケーションでクリックスルーURLをブラウザーで開きます。

      デスクトッププラットフォームでは、ビデオ広告の再生領域を使用して、ユーザーのクリック時にクリックスルーURLを呼び出します。
   * ユーザーを外部モバイルWebブラウザーにリダイレクトします。

      モバイルデバイスでは、ビデオ広告の再生領域は、コントロールの表示と非表示、再生の一時停止、フルスクリーンへの拡張など、他の機能に使用されます。 これらのデバイスでは、スポンサーボタンなどの別のビューを使用して、クリックスルーURLが起動されます。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じ、ビデオの再生を再開します。

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

例：

```java
private AdStartedEventListener adStartedEventListener = new AdStartedEventListener() { 
    @Override 
    public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        if (ad == null) { 
            return; 
        } 
 
        _pubOverlay.startAd(adPlaybackEvent.getAdBreak(), ad); 
 
        if (areClickableAdsEnabled() && ad.isClickable()) { 
            _isClickableAdPlaying = true; 
            _playerClickableAdFragment.show(); 
        } 
 
    } 
}; 
 
private AdCompletedEventListener adCompletedEventListener = new AdCompletedEventListener() { 
    @Override 
    public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { 
        Ad ad = adPlaybackEvent.getAd(); 
        _pubOverlay.stopAd(adPlaybackEvent.getAdBreak(), ad); 
 
        _isClickableAdPlaying = false; 
        if (ad.isClickable()) { 
            _playerClickableAdFragment.hide(); 
        } 
    } 
}; 
 
private AdClickedEventListener adClickedEventListener = new AdClickedEventListener() { 
    @Override 
    public void onAdClicked(AdClickEvent adClickEvent) { 
        AdClick adClick = adClickEvent.getAdClick(); 
        Ad ad = adClickEvent.getAd(); 
 
        String url = adClick.getUrl(); 
        if (url == null || url.trim().equals("")) { 
        } else { 
            Uri uri = Uri.parse(url); 
            Intent intent = new Intent(ACTION_VIEW, uri); 
            try { 
                startActivity(intent); 
            } catch (Exception e) { 
            } 
        } 
 
    } 
}; 
```

