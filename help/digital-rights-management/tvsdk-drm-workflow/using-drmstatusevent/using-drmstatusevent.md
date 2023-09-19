---
title: DRMStatusEvent クラスの使用：概要
description: DRMStatusEvent クラスの使用：概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# DRMStatusEvent クラスの使用：概要 {#using-the-drmstatusevent-class-overview}

A `DRMStatusEvent` オブジェクトは、Primetime DRM で保護されたコンテンツの再生が正常に開始した場合にディスパッチされます。 （成功とは、ライセンスが検証され、ユーザーがコンテンツの表示を認証され、承認されていることを意味します）。

The `DRMStatusEvent` オブジェクトには、ライセンスをオフラインで使用できるか、ライセンスの有効期限が切れてコンテンツを表示できなくなった場合など、ライセンスに関する情報が含まれます。
