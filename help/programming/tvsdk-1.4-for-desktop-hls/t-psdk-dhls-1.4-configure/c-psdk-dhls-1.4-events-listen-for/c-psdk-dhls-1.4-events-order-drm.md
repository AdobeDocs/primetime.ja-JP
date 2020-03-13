---
description: TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。
seo-description: TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。
seo-title: DRMイベント
title: DRMイベント
uuid: 729fe524-1047-4188-b4e6-96bfc5af4ae0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# DRMイベント{#drm-events}

TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。

すべてのDRM関連イベントに関する通知を受け取るには、以下をリッスンします。

```
DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE
```

次の例に、一般的な流れを示します。

```
mediaPlayer.addEventListener(DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE,  
                             onDRMMetadataInfoAvailable);   
private function onDRMMetadataInfoAvailable(event:DRMMetadataInfoEvent){ 
    var drmMetadataInfo:DRMMetadataInfo = event.drmMetadataInfo; 
    ... 
} 
```

