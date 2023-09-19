---
description: VPAID 2.0 サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。
title: VPAID 2.0 統合の実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# VPAID 2.0 統合の実装 {#implement-vpaid-integration}

VPAID 2.0 サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。

1. プレーヤーが PREPARED 状態の場合、カスタム広告ビューをプレーヤーインターフェイスに追加します。

   ```java
   ... 
   private FrameLayout _playerFrame; 
       ... 
       case PREPARED: 
           ... 
           addCustomView(); 
   ... 
   private void addCustomView() { 
       ... 
       WebView view = (WebView)_mediaPlayer.getCustomAdView(); 
       ... 
       _playerFrame.addView(view);
   ```

1. リスナーを作成し、 [イベント](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   >[!IMPORTANT]
   >
   >VPAID 2.0 ワークフローでは、カスタム広告ビューの場合、 `CustomAdView` ～の中でインスタンスを作る `AdBreak` 開始（イベント） `AD_BREAK_START`) および `AdBreak` 完了（イベント） `AD_BREAK_COMPLETE`) をクリックし、カスタム広告ビューを作成した時点から破棄する時点までの間、をクリックします。 つまり、すべての広告ブレークの開始時にカスタム広告ビューを作成し、すべての広告ブレークの完了時にカスタム広告ビューを破棄しないでください。
   >
   >
   >また、プレーヤーが PREPARED 状態の場合にのみ、カスタム広告ビューを作成する必要があります。
   >
   >
   >リセットが呼び出されたときにのみ、カスタム広告ビューを破棄します。 例：
   >
   >```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```
   >
   >最後に、カスタム広告ビューを破棄する前に、カスタム広告ビューを `FrameLayout`. 例：
   >
   >```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
