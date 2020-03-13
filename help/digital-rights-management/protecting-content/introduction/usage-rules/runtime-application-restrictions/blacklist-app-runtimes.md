---
description: 'null'
seo-description: 'null'
seo-title: アプリケーションランタイムのブラックリスト
title: アプリケーションランタイムのブラックリスト
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# アプリケーションランタイムのブラックリスト{#blacklist-of-application-runtimes}

アプリケーションランタイムのブラックリストは、コンテンツにアクセスできないPrimetimeクライアントまたはFlash Runtimeのバージョンを指定します。 制限付きランタイム（Flash Player、AIRまたはiOS）、プラットフォームおよびバージョンを指定します。

使用例：Primetime DRMクライアントのブラックリストと同様に、最新バージョンのFlash Player、AIRまたはiOSランタイムを、ライセンスの取得とコンテンツの再生に必要な最小バージョンとして指定できます。

次の属性に加え、Primetime DRMクライアントのバージョンでサポートされている属性でアプリケーションランタイムを識別できます。

| **属性** | **サポートされる値** | **一致条件** | **説明** |
|---|---|---|---|
| 申し込み | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | 完全一致 | アプリケーションランタイムの名前を指定します。 |

