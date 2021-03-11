---
description: TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。
title: DRMイベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# DRMイベント{#drm-events}

TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。

DRM関連のイベント通知をすべて受け取るには、以下をリッスンします。

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

