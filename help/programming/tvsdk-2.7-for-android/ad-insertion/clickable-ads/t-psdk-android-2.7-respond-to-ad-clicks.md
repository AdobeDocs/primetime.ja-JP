---
description: ユーザーが広告または関連するボタンをクリックすると、アプリケーションは応答する必要があります。 TVSDK は、クリックのリンク先 URL に関する情報を提供します。
title: 広告のクリック数への応答
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# 広告のクリック数への応答 {#respond-to-clicks-on-ads}

TVSDK は、クリックスルー広告に対して行動できるように情報を提供します。 プレーヤー UI を作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

Android 向け TVSDK の場合、リニア広告のみがクリック可能です。
ユーザーが広告または関連するボタンをクリックすると、アプリケーションは応答する必要があります。 TVSDK は、クリックのリンク先 URL に関する情報を提供します。

1. TVSDK 用のイベントリスナーを設定し、クリックスルー情報を提供するには、を登録します。 `AdClickedEventListener.onAdClicked`.

   ユーザーが広告または関連するボタンをクリックすると、 TVSDK は、クリックの宛先に関する情報を含め、この通知をディスパッチします。
1. クリック可能な広告に対するユーザーインタラクションを監視します。
1. ユーザーが広告やボタンをタッチまたはクリックして、TVSDK に通知する際に、を呼び出します。 `notifyClick` の `MediaPlayerView`.
1. をリッスンします。 `onAdClick(AdClickEvent event)` イベントを TVSDK から取得します。
1. クリックスルー URL および関連情報を取得するには、 `AdClickEvent` インスタンス。
1. ビデオを一時停止します。

   ビデオの一時停止について詳しくは、「再生の一時停止 — 再開」を参照してください。
1. クリックスルー情報を使用して、広告クリックスルー URL と関連情報を表示します。

       例えば、次のいずれかの方法で情報を表示できます。
   
   * アプリケーションで、ブラウザーでクリックスルー URL を開く。

     デスクトッププラットフォームでは、ビデオ広告の再生領域を使用して、ユーザーのクリック時にクリックスルー URL を呼び出します。
   * ユーザーを外部のモバイル Web ブラウザーにリダイレクトします。

     モバイルデバイスでは、ビデオ広告の再生領域は、コントロールの非表示と表示、再生の一時停止、フルスクリーンへの拡張など、他の機能に使用されます。 これらのデバイスでは、スポンサーボタンなどの別のビューを使用して、クリックスルー URL を起動します。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じ、ビデオの再生を再開します。

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
