---
description: Adobe Primetime ad decisioningでは、広告をキーと値のペアでターゲット設定できます。
seo-description: Adobe Primetime ad decisioningでは、広告をキーと値のペアでターゲット設定できます。
seo-title: ターゲット情報
title: ターゲット情報
uuid: 72114bef-36a1-4f2d-92e8-59f4885d70d2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ターゲット情報{#targeting-information}

Adobe Primetime ad decisioningでは、広告をキーと値のペアでターゲット設定できます。

次のキーと値のペアをブラウザーTVSDKに渡すには：

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var targetingInfo = new AdobePSDK.Metadata(); 
 
// Add key value pairs to targetingInfo 
targetingInfo.setValue(key1, value1); 
targetingInfo.setValue(key2, value2); 
 
auditudeSettings.targetingInfo = targetingInfo;
```

