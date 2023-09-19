---
description: Adobe Primetime Ad Decisioning では、キーと値のペアで広告のターゲットを設定できます。
title: ターゲティング情報
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---

# ターゲティング情報{#targeting-information}

Adobe Primetime Ad Decisioning では、キーと値のペアで広告のターゲットを設定できます。

これらのキーと値のペアを Browser TVSDK に渡すには：

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```
