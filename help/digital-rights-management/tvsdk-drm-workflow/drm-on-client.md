---
seo-title: クライアントでのPrimetime DRM
title: クライアントでのPrimetime DRM
uuid: 472180ad-6596-4a24-aa51-7909a75a5e10
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# クライアントでのPrimetime DRM{#primetime-drm-on-the-client}

保護されたコンテンツを再生するPrimetime TVSDKアプリケーションは、最初にPrimetime DRM APIを呼び出して、ライセンスの消費と保護されたコンテンツの再生のワークフローを開始する必要があります。 このワークフローでは、クライアント上のPrimetime DRMが、保護されたコンテンツのメタデータからライセンスリクエストを作成し、Primetime DRMライセンスサーバーに送信します。

ライセンス要求を発行する前に、必要に応じて（ビジネスルールに応じて）クライアントが認証/認証を行うことができます。
