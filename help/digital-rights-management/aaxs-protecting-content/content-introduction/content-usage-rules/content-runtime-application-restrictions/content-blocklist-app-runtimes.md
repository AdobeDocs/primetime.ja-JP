---
seo-title: 保護されたコンテンツへのアクセスが制限されたアプリケーションの実行時のブロックリスト
title: 保護されたコンテンツへのアクセスが制限されたアプリケーションの実行時のブロックリスト
uuid: 462a2c09-b335-4768-bd0e-1359db169d69
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# 保護されたコンテンツへのアクセスが制限されたアプリケーションの実行時のブロックリスト {#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

コンテンツにアクセスできないPrimetimeまたはFlash Runtimeのバージョンを指定します。 制限付きランタイム（Flash Player、AIRまたはiOS）、プラットフォームおよびバージョンを指定します。

使用例： DRMクライアントブロックリストと同様に、Flash Player、AIRまたはiOSランタイムの最新バージョンを、ライセンスの取得とコンテンツの再生に必要な最小限のバージョンとして指定できます。

アプリケーションランタイムは、以下の属性に加え、DRMクライアントバージョンでサポートされている属性で識別できます。

| **属性** | **サポートされる値** | **一致条件** | **説明** |
|---|---|---|---|
| 申し込み | &quot;FlashPlayer&quot;、&quot;AIR&quot;、&quot;DRM_Library&quot;、&quot;AVE&quot; | 完全一致 | アプリケーションランタイムの名前を指定します。 |
