---
description: TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。
title: DRM イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# DRM イベント{#drm-events}

TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。

すべての DRM 関連イベントに関する通知を受け取るには、 `MediaPlayer.DRMEventListener` には次のコールバックが含まれます。

| イベント | 意味 |
|---|---|
| [onDRMMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html#onDRMMetadata(DRMMetadataInfo)) `(DRMMetadataInfo drmMetadataInfo)` | 新しい DRM メタデータを使用できます。 |
