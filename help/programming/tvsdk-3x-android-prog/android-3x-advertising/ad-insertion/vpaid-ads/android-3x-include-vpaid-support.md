---
description: VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。
seo-description: VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。
seo-title: VPAID 2.0統合の実装
title: VPAID 2.0統合の実装
uuid: d512fb5b-001c-4a7a-a553-d5962002bb30
translation-type: tm+mt
source-git-commit: 83df68905f74931355264661aed6cff43b802d3f
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 2%

---


# VPAID 2.0統合の実装{#implement-vpaid-integration}

VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。

1. プレ追加イヤーがPREPARED状態の場合に、プレイヤーインターフェイスに対するカスタム広告表示。

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

1. リスナーを作成し、[イベント](../../../../tvsdk-3x-android-prog/android-3x-events-notifications/events-summary/android-3x-events-summary.md)で説明されているイベントを処理します。

   >[!IMPORTANT]
   >
   >VPAID 2.0ワークフローでは、カスタム広告表示の場合、カスタム広告表示を作成してから破棄するまで、`AdBreak`開始(イベント`AD_BREAK_START`)と`AdBreak`完了(イベント`AD_BREAK_COMPLETE`)にわたって`CustomAdView`インスタンスを維持することが非常に重要です。 つまり、各広告ブレーク開始にカスタム広告表示を作成し、完了するたびにその広告ブレークを破棄しないでください。
   >
   >
   >また、プレイヤーがPREPARED状態の場合、カスタム広告表示を作成する必要があります。
   >
   >
   >リセットが呼び出された場合にのみ、カスタム広告表示を破棄します。 例：
   >
   >
   ```
   >// on reset 
   >if (_mediaPlayer != null) { 
   >       _mediaPlayer.disposeCustomAdView(); 
   >       ... 
   >} 
   >
   >```
   >
   >最後に、カスタム広告表示を破棄する前に、`FrameLayout`から削除する必要があります。 例：
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
