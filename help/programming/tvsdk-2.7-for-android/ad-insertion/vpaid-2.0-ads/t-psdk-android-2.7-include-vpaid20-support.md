---
description: VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。
seo-description: VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。
seo-title: VPAID 2.0統合の実装
title: VPAID 2.0統合の実装
uuid: fa5b9cdd-e684-4656-91b7-50781dc59e23
translation-type: tm+mt
source-git-commit: 25f97c8d296f71deddc8f9d12b97007ddf73f603

---


# VPAID 2.0統合の実装 {#implement-vpaid-integration}

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
   >VPAID 2.0ワークフローでは、カスタム広告表示の場合、カスタム広告表示を作成してから破棄するまで、開始(イベント `CustomAdView` )と完了(イベント `AdBreak``AD_BREAK_START``AdBreak``AD_BREAK_COMPLETE`)の間でインスタンスを維持することが非常に重要です。 つまり、すべての広告の時間の開始でカスタム広告表示を作成し、完了するたびに広告の時間のを破棄しないでください。
   >
   >
   >また、プレイヤーがPREPARED状態の場合にのみ、カスタム広告表示を作成する必要があります。
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
   >最後に、カスタム広告表示を削除する前に、 `FrameLayout`例：
   >
   >
   ```
   >if (_playerFrame != null) 
   >       _playerFrame.removeAllViews(); 
   >```
