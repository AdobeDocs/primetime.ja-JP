---
description: VMAP インライン広告に無効なメディアタイプが含まれている場合、フォールバックを有効にすることができます。
title: VMAP インライン広告のフォールバック広告動作の定義
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# VMAP インライン広告のフォールバック広告動作の定義 {#define-fallback-ad-behavior-for-vmap-inline-ads}

VMAP インライン広告に無効なメディアタイプが含まれている場合、フォールバックを有効にすることができます。

1. 設定 `setFallbackOnInvalidCreativeEnabled` から `true` リニア/インライン広告のメディアタイプが HLS に対して無効な場合に、VMAP をフォールバックします。

   デフォルト値は `false`. リニア広告が無効なメディアタイプがある、または広告を再パッケージできないために失敗した場合、このフラグを使用すると、Primetime 広告決定は、広告が空の VAST ラッパーであった場合と同じフォールバック動作に従うことができます。

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```
