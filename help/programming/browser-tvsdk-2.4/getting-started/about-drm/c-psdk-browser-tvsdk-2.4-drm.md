---
description: Digital Rights Management(DRM)固有のワークフローを完了できます。
seo-description: Digital Rights Management(DRM)固有のワークフローを完了できます。
seo-title: Digital Rights Management
title: Digital Rights Management
uuid: 011605c7-50c4-4ad5-9961-8cd92d0e6fd8
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96
workflow-type: tm+mt
source-wordcount: '114'
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