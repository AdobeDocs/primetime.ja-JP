---
description: 'null'
seo-description: 'null'
seo-title: 保護されたコンテンツの再生が許可されたPrimetime DRMアプリケーションの許可リスト
title: 保護されたコンテンツの再生が許可されたPrimetime DRMアプリケーションの許可リスト
uuid: 23dd4faf-7992-4ee9-97ce-c6004ee995c2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# 保護されたコンテンツの再生が許可されたPrimetime DRMアプリケーションの許可リスト{#allowlist-for-primetime-drm-applications-allowed-to-play-protected-content}

許可リストは、コンテンツの再生が許可されるAIR、iOS、Androidアプリケーションを指定します。 また、AIRおよびiOSアプリケーションID、最小バージョン、最大バージョン、発行者IDも指定します。

使用例：特定のアプリケーションに再生を制限する場合や、コンテンツにアクセスできるアプリケーションのバージョンを制御する場合に、このルールを使用します。

>[!NOTE]
>
>AdobeFlash Builderを使用して保護されたアプリケーションを構築する場合は、アプリケーションをデバッグモードでデプロイしないようにする必要があります。 アプリケーションをデバッグモードでデプロイすると、Flash BuilderがAIRアプリケーション IDに`.debug`を追加するので、Primetime DRMの許可リスト機能が予期せず動作します。
