---
description: VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。
title: VPAID 2.0統合の実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---


# VPAID 2.0統合の実装{#implement-vpaid-integration}

VPAID 2.0サポートを追加するには、カスタム広告表示と適切なリスナーを追加します。

VPAID 2.0サポートを追加するには：

1. プレ追加イヤーインターフェイスへのカスタム広告表示。

   ```java
   _playerFrame.addView(mediaPlayer.createCustomAdView());
   ```

1. カスタム広告イベント追加のリスナー。

   ```java
   mediaplayer.addEventListener(MediaPlayer.Event.CUSTOM_AD,  
     _customAdEventListener);
   ```

