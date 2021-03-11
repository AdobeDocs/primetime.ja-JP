---
description: Adobe Primetimead decisioningでは、キーと値のペアに対して広告をターゲットできます。
title: ターゲット情報
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# ターゲット情報{#targeting-information}

Adobe Primetimead decisioningでは、キーと値のペアに対して広告をターゲットできます。

次のキーと値のペアをBrowser TVSDKに渡すには：

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```

