---
title: HTTPS経由のセキュアな広告読み込み
description: HTTPS経由のセキュアな広告読み込み
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---


# HTTPSを介したセキュアな広告読み込み{#secure-ad-loading-over-https}

Adobe Primetimeは、Primetime広告サーバーへの最初の呼び出しと、HTTPSを介したCRS関連の呼び出しをリクエストするオプションを提供します。

この機能は、デフォルトでは有効になっていません。 セキュアな広告読み込みを有効にするには、次を使用します。

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
