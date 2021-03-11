---
title: Primetime DRM（クライアントでの使用）
description: Primetime DRM（クライアントでの使用）
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# クライアントでのPrimetime DRM{#primetime-drm-on-the-client}

保護されたコンテンツを再生するPrimetime TVSDKアプリケーションは、最初にPrimetime DRM APIを呼び出して、ライセンス消費および保護されたコンテンツ再生のワークフローを開始する必要があります。 このワークフローでは、クライアントのPrimetime DRMが保護されたコンテンツのメタデータからライセンスリクエストを作成し、Primetime DRMライセンスサーバーに送信します。

ライセンス要求を発行する前に、必要に応じて（ビジネスルールに応じて）クライアントが認証/認証を行うことができます。
