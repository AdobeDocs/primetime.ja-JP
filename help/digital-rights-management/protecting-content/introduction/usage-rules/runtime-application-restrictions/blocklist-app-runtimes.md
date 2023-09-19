---
title: アプリケーションランタイムのブロックリスト
description: アプリケーションランタイムのブロックリスト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# アプリケーションランタイムのブロックリスト {#blocklist-of-application-runtimes}

ブロックリストのアプリケーションランタイムは、コンテンツにアクセスできない Primetime クライアントまたはFlashランタイムのバージョンを指定します。 制限されたランタイム (Flash Player、AIRまたはiOS)、プラットフォームおよびバージョンを指定します。

使用例： Primetime DRM クライアントブロックリストと同様に、Flash Player、AIRまたはiOSのランタイムの最新バージョンを、ライセンスの取得とコンテンツの再生に必要な最小バージョンとして指定できます。

アプリケーションのランタイムは、次の属性に加えて、Primetime DRM クライアントバージョンでサポートされている任意の属性で識別できます。

| **属性** | **サポートされている値** | **一致条件** | **説明** |
|---|---|---|---|
| アプリ | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | 完全一致 | アプリケーションランタイムの名前を指定します。 |
