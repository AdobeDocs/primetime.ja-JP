---
title: HTTPS を介したセキュアな広告読み込み
description: HTTPS を介したセキュアな広告読み込み
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# HTTPS を介したセキュアな広告読み込み{#secure-ad-loading-over-https}

Adobe Primetimeは、プレーヤーが http でホストされている場合でも、https を使用してサードパーティ広告サーバーをリクエストできます。 Auditude広告リゾルバーフェーズでクライアントが探している https にアップグレードされるのは、これらの広告サーバー呼び出しのみです。

>[!NOTE]
>
>この機能は、Flashではサポートされていません。

セキュアな広告の読み込みを有効にするには、次を使用します。 デフォルトでは有効になっていません。

```
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.forceHttpsConfiguration.adServerCalls = true;
```
