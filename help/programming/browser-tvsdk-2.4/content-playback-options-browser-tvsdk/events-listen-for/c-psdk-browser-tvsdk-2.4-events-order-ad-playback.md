---
description: 再生に広告が含まれる場合、Browser TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。
title: 広告イベントの順序
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# 広告イベントの順序{#order-of-advertising-events}

再生に広告が含まれる場合、Browser TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

広告を再生する場合、イベントの順序は次のとおりです。

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* 次は、広告の時間内の各広告に対してディスパッチされます。

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` （広告の再生中に複数回）
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

次の例に、広告再生イベントの一般的な流れを示します。

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```

