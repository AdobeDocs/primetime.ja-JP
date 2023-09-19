---
description: TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。 プレーヤーは、これらのイベントに応じてアクションを実装できます。
title: DRM イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# DRM イベント{#drm-events}

TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。 プレーヤーは、これらのイベントに応じてアクションを実装できます。

DRM 関連のすべてのイベントに関する通知を受け取るには、以下をリッスンします。

```
DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE
```

次の例に、一般的な進行状況を示します。

```
mediaPlayer.addEventListener(DRMMetadataInfoEvent.DRM_METADATA_INFO_AVAILABLE,  
                             onDRMMetadataInfoAvailable);   
private function onDRMMetadataInfoAvailable(event:DRMMetadataInfoEvent){ 
    var drmMetadataInfo:DRMMetadataInfo = event.drmMetadataInfo; 
    ... 
} 
```
