---
description: 'null'
seo-description: 'null'
seo-title: アプリケーションの実行時のブロックリスト
title: アプリケーションの実行時のブロックリスト
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# アプリケーションの実行時のブロックリスト {#blocklist-of-application-runtimes}

アプリケーションランタイムのブロックリストは、コンテンツにアクセスできないPrimetimeクライアントまたはFlash Runtimeのバージョンを指定します。 制限付きランタイム（Flash Player、AIRまたはiOS）、プラットフォームおよびバージョンを指定します。

使用例： Primetime DRMクライアントブロックリストと同様に、Flash Player、AIRまたはiOSランタイムの最新バージョンを、ライセンスの取得とコンテンツの再生に必要な最小限のバージョンとして指定できます。

以下の属性に加え、Primetime DRMクライアントバージョンでサポートされている属性のいずれかによって、アプリケーションランタイムを識別できます。

| **属性** | **サポートされる値** | **一致条件** | **説明** |
|---|---|---|---|
| 申し込み | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | 完全一致 | アプリケーションランタイムの名前を指定します。 |

