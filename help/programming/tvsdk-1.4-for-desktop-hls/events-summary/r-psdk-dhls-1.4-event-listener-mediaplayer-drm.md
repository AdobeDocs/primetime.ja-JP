---
description: TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。
title: DRM イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# DRM イベント{#drm-events}

TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。

DRM 関連のすべてのイベントに関する通知を受け取るには、 `DRMMetadataInfoEvent` (DRM イベントの `MediaPlayer` オブジェクト。

| イベント | 意味 |
|---|---|
| DRMMetadataInfoEvent.[DRM_METADATA_INFO_AVAILABLE](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/DRMMetadataInfoEvent.html#DRM_METADATA_INFO_AVAILABLE) | 新しい DRM メタデータを使用できます。 |
