---
description: VMAPインライン広告に無効なメディアタイプが含まれる場合、フォールバックを有効にできます。
seo-description: VMAPインライン広告に無効なメディアタイプが含まれる場合、フォールバックを有効にできます。
seo-title: VMAPインライン広告のフォールバック広告動作の定義
title: VMAPインライン広告のフォールバック広告動作の定義
uuid: bc8cb0b4-5ea9-429b-ab5d-746c6f03e74b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# VMAPインライン広告のフォールバック広告動作の定義{#define-fallback-ad-behavior-for-vmap-inline-ads}

VMAPインライン広告に無効なメディアタイプが含まれる場合、フォールバックを有効にできます。

1. `setFallbackOnInvalidCreativeEnabled`を`true`に設定し、リニア/インライン広告のメディアタイプがHLSに対して無効な場合にVMAPフォールバックを行います。

   デフォルト値は`false`です。 リニア広告が無効なメディアタイプを持つことや、広告を再パッケージできないことが原因でリニア広告が失敗した場合、このフラグを使用すると、Primetime広告が空のVASTラッパーであった場合と同じフォールバック動作に従うことができます。

   ```java
   AuditudeSettings result = new AuditudeSettings(); 
   result.setFallbackOnInvalidCreative(true);
   ```
