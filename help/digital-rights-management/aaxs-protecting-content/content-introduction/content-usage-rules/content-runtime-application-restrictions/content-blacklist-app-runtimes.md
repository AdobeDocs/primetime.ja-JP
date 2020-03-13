---
seo-title: 保護されたコンテンツへのアクセスが制限されたアプリケーションランタイムのブラックリスト
title: 保護されたコンテンツへのアクセスが制限されたアプリケーションランタイムのブラックリスト
uuid: 462a2c09-b335-4768-bd0e-1359db169d69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 保護されたコンテンツへのアクセスが制限されたアプリケーションランタイムのブラックリスト {#blacklist-of-application-runtimes-restricted-from-accessing-protected-content}

コンテンツにアクセスできないPrimetimeまたはFlash Runtimeのバージョンを指定します。 制限付きランタイム（Flash Player、AIRまたはiOS）、プラットフォームおよびバージョンを指定します。

使用例：DRMクライアントブラックリストと同様に、最新バージョンのFlash Player、AIRまたはiOSランタイムを、ライセンスの取得とコンテンツの再生に必要な最小バージョンとして指定できます。

アプリケーションランタイムは、次の属性に加え、DRMクライアントのバージョンでサポートされている属性で識別できます。

| **属性** | **サポートされる値** | **一致条件** | **説明** |
|---|---|---|---|
| 申し込み | &quot;FlashPlayer&quot;、&quot;AIR&quot;、&quot;DRM_Library&quot;、&quot;AVE&quot; | 完全一致 | アプリケーションランタイムの名前を指定します。 |

