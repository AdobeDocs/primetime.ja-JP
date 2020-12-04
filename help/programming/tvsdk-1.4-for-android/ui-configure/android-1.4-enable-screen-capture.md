---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: 画面キャプチャを有効にする
title: 画面キャプチャを有効にする
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# 画面キャプチャを有効にする{#enable-screen-capture}

TVSDKは、デフォルトで画面のキャプチャを許可しません。 プレイヤーは、構築時に`com.adobe.ave.VideoEngineView`オブジェクトに対して`setSecure(true)`を呼び出します。 `VideoEngineView`オブジェクトを作成して`VideoEngine`オブジェクトに渡す必要があるので、このオブジェクトにアクセスできます。

アプリで画面キャプチャを有効にするには：

1. `com.adobe.ave.VideoEngineView`オブジェクトを作成します。
1. `VideoEngineView`オブジェクトで`setSecure(false)`を呼び出します。
