---
description: VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。
title: VPAID 2.0統合の実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 2%

---


# VPAID 2.0統合の実装{#implement-vpaid-integration}

VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。

VPAID 2.0サポートを追加するには：

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

1. リスナーを作成し、イベントリスナーで説明されているイベントを処理します。

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
   >```
   >
   >最後に、カスタム広告表示を破棄する前に、`FrameLayout`から削除する必要があります。 例：
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
