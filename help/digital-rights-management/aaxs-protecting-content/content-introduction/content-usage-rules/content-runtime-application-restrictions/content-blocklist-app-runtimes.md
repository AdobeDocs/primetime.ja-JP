---
title: 保護されたコンテンツへのアクセスが制限されたアプリケーションの実行時のブロックリスト
description: 保護されたコンテンツへのアクセスが制限されたアプリケーションの実行時のブロックリスト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# 保護されたコンテンツへのアクセスが制限されたアプリケーションの実行時のブロックリスト{#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

コンテンツにアクセスできないPrimetimeまたはFlashランタイムのバージョンを指定します。 制限付きランタイム(Flash Player、AIRまたはiOS)、プラットフォームおよびバージョンを指定します。

使用例：DRMクライアントブロックリストと同様に、Flash Player、AIR、またはiOSランタイムの最新バージョンを、ライセンスの取得とコンテンツの再生に必要な最小限のバージョンとして指定できます。

アプリケーションランタイムは、以下の属性に加え、DRMクライアントバージョンでサポートされている属性で識別できます。

| **属性** | **サポートされる値** | **一致条件** | **説明** |
|---|---|---|---|
| 申し込み | &quot;FlashPlayer&quot;、&quot;AIR&quot;、&quot;DRM_Library&quot;、&quot;AVE&quot; | 完全一致 | アプリケーションランタイムの名前を指定します。 |
