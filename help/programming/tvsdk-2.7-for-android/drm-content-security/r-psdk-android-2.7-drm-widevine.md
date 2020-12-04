---
description: DASHストリームにAndroidネイティブWidevine DRMを使用できます。
seo-description: DASHストリームにAndroidネイティブWidevine DRMを使用できます。
seo-title: Widevine DRM
title: Widevine DRM
uuid: ceb2f18f-9e53-47d6-9d4b-7004ac1d22c9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---


# Widevine DRM {#widevine-drm}

DASHストリームにAndroidネイティブWidevine DRMを使用できます。

再生を開始する前に、次の`com.adobe.mediacore.drm.DRMManager` APIを呼び出します。

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

引数：

* `drm` - Widevine `"com.widevine.alpha"` の場合。

* `licenseServerURL`  — ライセンス要求を受け取るWidevineライセンスサーバーのURL。
* `requestProperties`  — 発信ライセンス要求に含める追加のヘッダが含まれます。

例えば、ExpressPlay DRM用にパッケージ化されたコンテンツを使用する場合、再生の前に次のコードを使用します。

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```

