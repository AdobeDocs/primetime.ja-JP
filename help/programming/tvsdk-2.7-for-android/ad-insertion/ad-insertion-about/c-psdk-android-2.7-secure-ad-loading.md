---
title: HTTPS を介したセキュアな広告読み込み
description: HTTPS を介したセキュアな広告読み込み
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# HTTPS を介したセキュアな広告読み込み {#secure-ad-loading-over-https}

Adobe Primetimeには、Primetime 広告サーバーへの最初の呼び出しと、HTTPS を介した CRS 関連の呼び出しをリクエストするオプションが用意されています。

この機能は、デフォルトでは有効になっていません。 セキュアな広告の読み込みを有効にするには、次を使用します。

```
AuditudeSettings auditudeSettings = new AuditudeSettings(); 
auditudeSettings. getForceHttpsConfiguration().setAdServerCalls(true);
```
