---
description: 'null'
keywords: setSecure;VideoEngineView
seo-description: 'null'
seo-title: 画面キャプチャの有効化
title: 画面キャプチャの有効化
uuid: f3d18729-e13e-47f9-b4b8-f93a2874ef16
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 画面キャプチャの有効化{#enable-screen-capture}

TVSDKは、デフォルトで画面のキャプチャを許可しません。 プレイヤーは、構築時 `setSecure(true)` にオブジェクト `com.adobe.ave.VideoEngineView` を呼び出します。 オブジェクトを作成し、オブジェクトに渡すのと同様に、このオ `VideoEngineView` ブジェクトにアクセスでき `VideoEngine` ます。

アプリで画面キャプチャを有効にするには：

1. オブジェクトを作 `com.adobe.ave.VideoEngineView` 成します。
1. オブジェ `setSecure(false)` クトを呼び `VideoEngineView` 出します。
