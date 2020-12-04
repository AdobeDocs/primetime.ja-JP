---
description: 'null'
seo-description: 'null'
seo-title: HTTPS経由のセキュアな広告読み込み
title: HTTPS経由のセキュアな広告読み込み
uuid: 0d680fef-a372-4157-a89b-d9f10003c768
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# HTTPS{#secure-ad-loading-over-https}を介したセキュアな広告読み込み

Adobe Primetimeは、Primetime広告サーバーへの最初の呼び出しと、HTTPSを介したCRS関連の呼び出しをリクエストするオプションを提供します。

この機能は、デフォルトでは有効になっていません。 セキュアな広告読み込みを有効にするには、次を使用します。

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

