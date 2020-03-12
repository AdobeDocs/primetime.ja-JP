---
description: VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。
seo-description: VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。
seo-title: VPAID 2.0統合の実装
title: VPAID 2.0統合の実装
uuid: d512fb5b-001c-4a7a-a553-d5962002bb30
translation-type: tm+mt
source-git-commit: 1034a0520590777cc0930d2f732741202bc3bc04

---


# VPAID 2.0統合の実装 {#implement-vpaid-integration}

VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。

1. プレイヤーがPREPARED状態の場合に、カスタム広告ビューをプレーヤーインターフェイスに追加します。

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

1. リスナーを作成し、イベントで説明されているイベントを処 [理します](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md)。

   >[!IMPORTANT]
   >
   >VPAID 2.0ワークフローでは、カスタム広告ビューの場合、カスタム広告ビューを作成した時点から破棄する時点まで、開始(イベント `CustomAdView` )と完了(イベント `AdBreak``AD_BREAK_START``AdBreak``AD_BREAK_COMPLETE`)の間でインスタンスを維持することが非常に重要です。 つまり、広告の時間の開始ごとにカスタム広告ビューを作成し、広告の時間の完了ごとにその広告ビューを破棄しないでください。
   >
   >
   >さらに、プレイヤーがPREPARED状態の場合にのみ、カスタム広告ビューを作成します。
   >
   >
   >リセットが呼び出された場合にのみ、カスタム広告ビューを破棄します。 例：   >
   >
   >
   ```>
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```

   最後に、カスタム広告ビューを破棄する前に、カスタム広告ビューをから削除する必要がありま `FrameLayout`す。 例：
   >```
   >if (_playerFrame != null) 
      _playerFrame.removeAllViews(); 
   ```
