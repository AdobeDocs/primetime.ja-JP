---
title: 保護されたコンテンツの再生が許可された Primetime DRM アプリケーションの許可リスト
description: 保護されたコンテンツの再生が許可された Primetime DRM アプリケーションの許可リスト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# 保護されたコンテンツの再生が許可された Primetime DRM アプリケーションの許可リスト {#allowlist-for-primetime-drm-applications-allowed-to-play-protected-content}

許可リストは、コンテンツの再生が許可されるAIR、iOSおよび Android のアプリケーションを指定します。 また、AIRおよびiOSアプリケーション ID、最小バージョン、最大バージョン、発行者 ID も指定します。

使用例：このルールを使用して、特定のアプリケーションでの再生を制限したり、コンテンツにアクセスできるアプリケーションのバージョンを制御したりします。

>[!NOTE]
>
>AdobeFlash Builderを使用して保護されたアプリケーションを構築する場合は、アプリケーションをデバッグモードでデプロイしないようにする必要があります。 デバッグモードでアプリケーションをデプロイすると、Flash Builderによって `.debug` をAIRアプリケーション ID に追加すると、Primetime DRM の許可リスト機能が予期せず動作します。
