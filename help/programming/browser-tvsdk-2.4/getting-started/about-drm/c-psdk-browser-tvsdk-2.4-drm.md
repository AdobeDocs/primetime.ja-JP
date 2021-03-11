---
description: Digital Rights Management(DRM)固有のワークフローを完了できます。
title: Digital Rights Management
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Digital Rights Management{#digital-rights-management}

Digital Rights Management(DRM)固有のワークフローを完了できます。

`AdobePSDK.DRMMetadataInfoEvent`イベントをリッスンしてDRMワークフローを処理できます。

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## 追加Digital Rights Management{#add-digital-rights-management}

1. 追加`DRMMetadataInfoAvailableEvent`を呼び出して`DRMMetadata`を取得します。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. 手順1の行の上に`onDRMMetadataInfoAvailable`セクションを実装します。

   ```js
   var onDRMMetadataInfoAvaialble = function(event) { 
    var drmMetadataInfo = event.drmMetadataInfo; 
    var drmMetadata = null; 
   
    if(drmMetadataInfo) { 
     drmMetadata = drmMetadataInfo.drmMetadata; 
    } 
   
    drmManager.acquireLicense(drmMetadata, null, null); 
   };
   ```

1. setupVideoメソッドでDRMManagerを作成します。

   ```js
   var drmManager = player.drmManager;
   ```

1. 以下のサンプルをコピーして、WidevineおよびPlayReady用の保護データを作成します。

   ```js
   var protectionData = { 
     "com.widevine.alpha":{ 
       "serverURL":"https://wv.service.expressplay.com/hms/wv/rights/? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]"  
     }, 
   
     "com.microsoft.playready":{ 
       "serverURL":"https://pr.test.expressplay.com/playready/RightsManager.asmx? 
                    ExpressPlayToken=[YOUR_EXPRESSPLAY_TOKEN]", 
         "httpRequestHeaders":{ 
       } 
     } 
   };
   ```

1. drmManager追加に保護データを送信します。

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. リソースURLをDASHテストストリームに変更します。

   >[!TIP]
   >
   >リソースタイプはDASHになっているので、必ず更新してください。

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. 設定をテストします。