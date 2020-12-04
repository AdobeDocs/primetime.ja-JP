---
description: 'null'
seo-description: 'null'
seo-title: HTTPS経由のセキュアな広告読み込み
title: HTTPS経由のセキュアな広告読み込み
uuid: 72ab94d3-ee0c-4f02-adf2-c186ae6aec26
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# HTTPSを介したセキュアな広告読み込み{#secure-ad-loading-over-https}

Adobe Primetimeは、Primetime広告サーバーへの最初の呼び出しと、HTTPSを介したCRS関連の呼び出しをリクエストするオプションを提供します。

この機能は、デフォルトでは有効になっていません。 セキュアな広告読み込みを有効にするには、次を使用します。

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```

