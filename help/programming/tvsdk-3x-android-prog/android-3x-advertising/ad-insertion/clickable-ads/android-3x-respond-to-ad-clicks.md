---
description: ユーザーが広告または関連するボタンをクリックした場合、アプリは応答する必要があります。 TVSDKは、クリック時のリンク先URLに関する情報を提供します。
title: 広告のクリックに対するレスポンス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# 広告のクリックに反応{#respond-to-clicks-on-ads}

TVSDKは、クリックスルー広告に対してアクションを実行できるように情報を提供します。 プレイヤーUIを作成する際、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

Android向けTVSDKの場合、リニア広告のみがクリック可能です。
ユーザーが広告または関連するボタンをクリックした場合、アプリは応答する必要があります。 TVSDKは、クリック時のリンク先URLに関する情報を提供します。

1. TVSDKのイベントリスナーを設定し、クリックスルー情報を提供するには、`AdClickedEventListener.onAdClicked`を登録します。

   ユーザーが広告または関連するボタンをクリックすると、TVSDKは、クリック先に関する情報を含む、この通知をディスパッチします。
1. クリック可能な広告に対するユーザーの操作を監視します。
1. ユーザーが広告やボタンをタッチまたはクリックしたら、TVSDKに通知するために、`MediaPlayerView`で`notifyClick`を呼び出します。
1. TVSDKの`onAdClick(AdClickEvent event)`イベントをリッスンします。
1. クリックスルーURLと関連情報を取得するには、`AdClickEvent`インスタンスのgetterメソッドを使用します。
1. ビデオを一時停止します。

   ビデオの一時停止について詳しくは、[再生の一時停止と再開](../../ad-insertion/clickable-ads/android-3x-pausing-resuming-playback.md)を参照してください。
1. クリックスルー情報を使用して、広告のクリックスルーURLと関連情報を表示します。 例えば、次のいずれかの方法で情報を表示できます。

   * アプリケーションで、ブラウザーでクリックスルーURLを開きます。

      デスクトッププラットフォームでは、ビデオ広告の再生領域は、ユーザーがクリックするとクリックスルーURLを呼び出すのに使用されます。
   * ユーザーを外部モバイルWebブラウザーにリダイレクトします。

      携帯端末では、ビデオ広告の再生領域は、コントロールの表示と非表示、再生の一時停止、フルスクリーンへの拡大など、他の機能に使用されます。 これらのデバイスでは、スポンサーボタンなどの別の表示を使用して、クリックスルーURLを起動します。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じて、ビデオの再生を再開します。

<!--<a id="example_2D93228E510D438C8AB5559897817A47"></a>-->

例：

```java
private AdStartedEventListener adStartedEventListener =  
  new AdStartedEventListener() { 
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
 
private AdCompletedEventListener adCompletedEventListener =  
  new AdCompletedEventListener() { 
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
 
private AdClickedEventListener adClickedEventListener =  
  new AdClickedEventListener() { 
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
