---
description: 再生に広告が含まれている場合、Browser TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。
title: 広告イベントの順序
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# 広告イベントの順序{#order-of-advertising-events}

再生に広告が含まれている場合、Browser TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

広告を再生する際のイベントの順序は次のとおりです。

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* 広告ブレークの各広告に対して、次の情報がディスパッチされます。

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` （広告の再生中に複数回）
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

次の例に、広告再生イベントの一般的な進行を示します。

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```
