---
title: アプリケーションの実行時のブロックリスト
description: アプリケーションの実行時のブロックリスト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# アプリケーションの実行時のブロックリスト{#blocklist-of-application-runtimes}

アプリケーションランタイムのブロックリストは、コンテンツにアクセスできないPrimetimeクライアントまたはFlashランタイムのバージョンを指定します。 制限付きランタイム(Flash Player、AIRまたはiOS)、プラットフォームおよびバージョンを指定します。

使用例：Primetime DRMクライアントブロックリストと同様、Flash Player、AIRまたはiOSランタイムの最新バージョンを、ライセンスの取得とコンテンツの再生に必要な最小バージョンとして指定できます。

以下の属性に加え、Primetime DRMクライアントバージョンでサポートされている属性のいずれかによって、アプリケーションランタイムを識別できます。

| **属性** | **サポートされる値** | **一致条件** | **説明** |
|---|---|---|---|
| 申し込み | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | 完全一致 | アプリケーションランタイムの名前を指定します。 |

