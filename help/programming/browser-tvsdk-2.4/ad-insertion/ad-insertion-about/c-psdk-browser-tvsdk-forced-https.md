---
description: 'null'
seo-description: 'null'
seo-title: HTTPS経由のセキュアな広告読み込み
title: HTTPS経由のセキュアな広告読み込み
uuid: 10657f59-cfbf-4c75-9249-fc154952bc51
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '73'
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
