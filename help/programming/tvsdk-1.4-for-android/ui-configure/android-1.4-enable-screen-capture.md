---
keywords: setSecure;VideoEngineView
title: スクリーンキャプチャを有効にする
description: スクリーンキャプチャを有効にする
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# スクリーンキャプチャを有効にする{#enable-screen-capture}

TVSDK は、デフォルトでは画面キャプチャを許可しません。 プレーヤーがを呼び出す `setSecure(true)` の `com.adobe.ave.VideoEngineView` オブジェクトを構築時に作成します。 このオブジェクトにアクセスするには、 `VideoEngineView` オブジェクトを作成し、それを `VideoEngine` オブジェクト。

アプリでスクリーンキャプチャを有効にするには：

1. を作成します。 `com.adobe.ave.VideoEngineView` オブジェクト。
1. 通話 `setSecure(false)` を `VideoEngineView` オブジェクト。
