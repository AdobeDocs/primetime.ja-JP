---
description: コードは、DRMManager を通じてキーをリクエストできます。
title: HTML5 TVSDK のキーリクエストワークフロー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# HTML5 TVSDK のキーリクエストワークフロー{#key-request-workflow-on-html-tvsdk}

コードは、DRMManager を通じてキーをリクエストできます。

また、Browser TVSDK は、DRMManager オブジェクトを介して setProtectionData API を公開します。

```
[  /** 
   * This will only work for MSE. 
   * <p> Attach key system specific data to use for DRM 
license acquisition. </p> 
   * @param {Object} protectionData - an object containing property names corresponding to key system name strings 
   * (e.g. "org.w3.clearkey") and associated values being instances of 
   * MediaPlayer.vo.protection.ProtectionData. 
   * @returns {AdobePSDK.PSDKErrorCode} kECSuccess or one of the error codes. 
   * @function 
   * @memberof AdobePSDK.DRMManager# 
   */ 
   setProtectionData: function(protectionData) 
```

通常の方法でコンテンツの再生を開始する前に、コードはこの API を呼び出す必要があります。 MediaPlayer.vo.protection.ProtectionData は、こちらに記載されています。 [https://vm2.dashif.org/dash.js/docs/jsdocs/MediaPlayer.vo.protection.ProtectionData.html](https://vm2.dashif.org/dash.js/docs/jsdocs/MediaPlayer.vo.protection.ProtectionData.html)

以下に、PlayReady と Widevine の両方のライセンスサーバー URL を持つ保護データオブジェクトの例を示します。

```
var protectionData = { 
   "com.widevine.alpha": { 
                          "serverURL": "https://wv.service.expressplay.com/hms/wv/rights/ 
                           ?ExpressPlayToken=AQAAABIDKA4AAABQuPPoebWWZZD2l3APRKkkagEDOXm 
                           CjgbhsqJTYeZ9KabkjCvSLvuXGHiVLymBnouGXDdCKpbz5IvB3jCZp9U05pys 
                           l9eavucsWXnA0tafbM-1SSJKXOa70kvxAJ_ybhdcmy7-6g" 
                          }, 
   "com.microsoft.playready": { 
                               "serverURL": "https://expressplay-licensing.axprod.net/ 
                                LicensingService.ashx?ExpressPlayToken=AQAAAw_ZXqcAAAB 
                                gHD1gnn_AMQJKfFCP3k9zbBw2srzBLryJVLXclnjhcSBCz4TBzrtfe 
                                gmSw1hAKdFHTNL-KVBGsI4ygBnfPRBUCvGsVOwpQ944fhq45W06ygJ 
                                roB2xOrM03tbkWcrthI7y_UQdHzufHjcBqKZm8QDoqKpxrxc" 
                               } 
   };
```

TVSDK は、特定の DRM システムを強制する API を提供しません。各ブラウザーは 1 つの DRM システムのみをサポートしているからです。
