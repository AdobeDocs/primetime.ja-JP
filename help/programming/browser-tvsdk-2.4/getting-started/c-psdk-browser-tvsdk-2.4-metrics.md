---
description: ブラウザーTVSDKは、分析およびデバッグに使用する指標を提供します。 これらの指標は、QoSProviderを使用して取得できます。
title: 指標
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 5%

---


# 指標{#metrics}

ブラウザーTVSDKは、分析およびデバッグに使用する指標を提供します。 これらの指標は、QoSProviderを使用して取得できます。

例：

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

