---
description: ブラウザーTVSDKは、分析およびデバッグに使用する指標を提供します。 これらの指標は、QoSProviderを使用して取得できます。
seo-description: ブラウザーTVSDKは、分析およびデバッグに使用する指標を提供します。 これらの指標は、QoSProviderを使用して取得できます。
seo-title: 指標
title: 指標
uuid: 4734e532-1f83-4691-b1bd-785f78e55d8d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 指標{#metrics}

ブラウザーTVSDKは、分析およびデバッグに使用する指標を提供します。 これらの指標は、QoSProviderを使用して取得できます。

例：

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```

