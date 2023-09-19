---
description: ブラウザー TVSDK は、分析とデバッグに使用する指標を提供します。 QoSProvider を使用して、これらの指標を取得できます。
title: 指標
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# 指標{#metrics}

ブラウザー TVSDK は、分析とデバッグに使用する指標を提供します。 QoSProvider を使用して、これらの指標を取得できます。

例：

```js
var qosProvider = new AdobePSDK.QOSProvider(); 
qosProvider.attachMediaPlayer(player); 
var metrics = qosProvider.playbackInformation;
```
