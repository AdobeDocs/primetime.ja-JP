---
title: HTTPS経由のセキュアな広告読み込み
description: HTTPS経由のセキュアな広告読み込み
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# HTTPSを介したセキュアな広告読み込み{#secure-ad-loading-over-https}

Adobe Primetimeは、プレーヤーがhttpでホストされている場合でも、httpsを使用してサードパーティの広告サーバーをリクエストできます。 httpsにアップグレードされた広告サーバー呼び出しのみが、Auditude Ad Resolverフェーズ中にクライアントがシークするものです。

>[!NOTE]
>
>この機能はFlashではサポートされていません。

セキュアな広告読み込みを有効にするには、次を使用します。 デフォルトでは有効になっていません。

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
