---
description: デジタル著作権管理(DRM)固有のワークフローを完了できます。
seo-description: デジタル著作権管理(DRM)固有のワークフローを完了できます。
seo-title: デジタル著作権管理
title: デジタル著作権管理
uuid: 011605c7-50c4-4ad5-9961-8cd92d0e6fd8
translation-type: tm+mt
source-git-commit: 5a786d8001326f874a51d65b8e8badca44f46e96

---


# デジタル著作権管理 {#digital-rights-management}

デジタル著作権管理(DRM)固有のワークフローを完了できます。

このイベントをリッスンして、DRMワ `AdobePSDK.DRMMetadataInfoEvent` ークフローを処理できます。

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## デジタル著作権管理の追加 {#add-digital-rights-management}

1. を追加して、 `DRMMetadataInfoAvailableEvent` を取得しま `DRMMetadata`す。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. 手順1の行 `onDRMMetadataInfoAvailable` の上のセクションを実装します。

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

1. 次のサンプルをコピーして、WidevineおよびPlayReadyの保護データを作成します。

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

1. drmManagerに保護データを追加します。

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