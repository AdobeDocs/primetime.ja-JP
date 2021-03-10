---
description: DASHストリームにAndroidネイティブWidevine DRMを使用できます。
title: Widevine DRM
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '72'
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

