---
description: 'null'
seo-description: 'null'
seo-title: HTTPS経由のセキュアな広告読み込み
title: HTTPS経由のセキュアな広告読み込み
uuid: 18be77cc-c59b-4982-b8c1-e4451495edd2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
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
