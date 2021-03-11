---
title: 保護されたコンテンツの再生が許可されたPrimetime DRMアプリケーションの許可リスト
description: 保護されたコンテンツの再生が許可されたPrimetime DRMアプリケーションの許可リスト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# 保護されたコンテンツの再生が許可されたPrimetime DRMアプリケーションの許可リスト{#allowlist-for-primetime-drm-applications-allowed-to-play-protected-content}

許可リストは、コンテンツの再生が許可されるAIR、iOS、Androidアプリケーションを指定します。 また、AIRおよびiOSアプリケーションID、最小バージョン、最大バージョン、発行者IDも指定します。

使用例：特定のアプリケーションに再生を制限する場合や、コンテンツにアクセスできるアプリケーションのバージョンを制御する場合に、このルールを使用します。

>[!NOTE]
>
>AdobeFlash Builderを使用して保護されたアプリケーションを構築する場合は、アプリケーションをデバッグモードでデプロイしないようにする必要があります。 アプリケーションをデバッグモードでデプロイすると、Flash BuilderがAIRアプリケーション IDに`.debug`を追加するので、Primetime DRMの許可リスト機能が予期せず動作します。
