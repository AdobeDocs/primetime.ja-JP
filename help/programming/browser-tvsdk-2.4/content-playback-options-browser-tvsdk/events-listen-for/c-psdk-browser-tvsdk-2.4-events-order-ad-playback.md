---
description: 再生に広告が含まれる場合、ブラウザーTVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。
seo-description: 再生に広告が含まれる場合、ブラウザーTVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。
seo-title: 広告イベントの順序
title: 広告イベントの順序
uuid: 9787e6ac-5e52-4d7d-8fc7-f7609633707c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 広告イベントの順序{#order-of-advertising-events}

再生に広告が含まれる場合、ブラウザーTVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。

<!--<a id="section_69E3CCBC57BB48399799876E83908348"></a>-->

広告を再生する場合、イベントの順序は次のとおりです。

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* 広告の時間内のすべての広告に対して、次がディスパッチされます。

   * `AdobePSDK.PSDKEventType.AD_STARTED`
   * `AdobePSDK.PSDKEventType.AD_PROGRESS` （広告の再生中に複数回）
   * `AdobePSDK.PSDKEventType.AD_COMPLETED`

* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`

次の例は、広告再生イベントの一般的な流れを示しています。

```js
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_STARTED, onAdbreakStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_STARTED, onAdStarted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_PROGRESS, onAdProgress); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_COMPLETED, onAdCompleted); 
player.addEventListener(AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED, onAdbreakCompleted);
```

