---
description: VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。
seo-description: VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。
seo-title: VPAID 2.0統合の実装
title: VPAID 2.0統合の実装
uuid: 7d11ffd8-240c-4a95-94e6-ff4417c8942e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# VPAID 2.0統合の実装{#implement-vpaid-integration}

VPAID 2.0サポートを追加するには、カスタム広告ビューと適切なリスナーを追加します。

VPAID 2.0サポートを追加するには：

1. カスタム広告ビューをプレーヤーインターフェイスに追加します。

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. カスタム広告イベントのリスナーを追加します。

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```

