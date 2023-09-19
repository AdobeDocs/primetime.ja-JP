---
title: クライアントでの Primetime DRM
description: クライアントでの Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# クライアントでの Primetime DRM{#primetime-drm-on-the-client}

保護されたコンテンツを再生する Primetime TVSDK アプリケーションは、まず Primetime DRM API を呼び出して、ライセンス消費のワークフローを開始し、コンテンツ再生を保護する必要があります。 このワークフローでは、クライアント上の Primetime DRM が保護されたコンテンツのメタデータからライセンスリクエストを作成し、Primetime DRM ライセンスサーバーに送信します。

ライセンスリクエストを発行する前に、クライアントは（ビジネスルールに応じて）必要な認証/承認を必要に応じて実行できます。
