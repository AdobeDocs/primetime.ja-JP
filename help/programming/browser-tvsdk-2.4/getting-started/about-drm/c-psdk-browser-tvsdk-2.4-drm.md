---
description: Digital Rights Management(DRM) 固有のワークフローを完了できます。
title: Digital Rights Management
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Digital Rights Management {#digital-rights-management}

Digital Rights Management(DRM) 固有のワークフローを完了できます。

次の情報を聞くことができます。 `AdobePSDK.DRMMetadataInfoEvent` DRM ワークフローを処理するイベント：

```js
... 
player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvailable);
...
```

## 追加Digital Rights Management {#add-digital-rights-management}

1. 次を追加： `DRMMetadataInfoAvailableEvent` 手に入れる `DRMMetadata`.

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.DRM_METADATA_INFO_AVAILABLE, onDRMMetadataInfoAvaialble);
   ```

1. の実装 `onDRMMetadataInfoAvailable` セクションを手順 1 の行の上に配置します。

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

1. setupVideo メソッドで DRMManager を作成します。

   ```js
   var drmManager = player.drmManager;
   ```

1. 次のサンプルをコピーして、Widevine および PlayReady の保護データを作成します。

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

1. drmManager に保護データを追加します。

   ```js
   drmManager.setProtectionData(protectionData);
   ```

1. リソース URL を DASH テストストリームに変更します。

   >[!TIP]
   >
   >リソースの種類は DASH になったので、必ず更新してください。

   ```js
   var resourceUrl = "https://ptdemos.com/videos/dashdrm/stream.mpd"; 
   var resourceType = AdobePSDK.MediaResourceType.DASH;
   ```

1. 設定をテストします。
