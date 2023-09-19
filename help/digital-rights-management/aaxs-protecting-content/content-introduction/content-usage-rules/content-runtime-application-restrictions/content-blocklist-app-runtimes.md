---
title: 保護されたコンテンツへのアクセスが制限されたアプリケーションランタイムのブロックリスト
description: 保護されたコンテンツへのアクセスが制限されたアプリケーションランタイムのブロックリスト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# 保護されたコンテンツへのアクセスが制限されたアプリケーションランタイムのブロックリスト {#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

コンテンツにアクセスできない Primetime またはFlashランタイムのバージョンを指定します。 制限されたランタイム (Flash Player、AIRまたはiOS)、プラットフォームおよびバージョンを指定します。

使用例： DRM クライアントブロックリストと同様に、Flash Player、AIR、iOSのランタイムの最新バージョンを、ライセンスの取得とコンテンツの再生に必要な最小バージョンとして指定できます。

アプリケーションランタイムは、次の属性に加えて、DRM クライアントバージョンでサポートされる属性のいずれかで識別できます。

| **属性** | **サポートされている値** | **一致条件** | **説明** |
|---|---|---|---|
| アプリ | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | 完全一致 | アプリケーションランタイムの名前を指定します。 |
