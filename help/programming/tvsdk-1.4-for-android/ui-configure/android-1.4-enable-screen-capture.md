---
keywords: setSecure;VideoEngineView
title: 画面キャプチャを有効にする
description: 画面キャプチャを有効にする
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# 画面キャプチャを有効にする{#enable-screen-capture}

TVSDKは、デフォルトで画面のキャプチャを許可しません。 プレイヤーは、構築時に`com.adobe.ave.VideoEngineView`オブジェクトに対して`setSecure(true)`を呼び出します。 `VideoEngineView`オブジェクトを作成して`VideoEngine`オブジェクトに渡す必要があるので、このオブジェクトにアクセスできます。

アプリで画面キャプチャを有効にするには：

1. `com.adobe.ave.VideoEngineView`オブジェクトを作成します。
1. `VideoEngineView`オブジェクトで`setSecure(false)`を呼び出します。
