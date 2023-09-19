---
description: Android のネイティブ Widevine DRM を DASH ストリームで使用できます。
title: Widevine DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

Android のネイティブ Widevine DRM を DASH ストリームで使用できます。

次の呼び出しをおこないます。 `com.adobe.mediacore.drm.DRMManager` 再生を開始する前の API:

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

引数：

* `drm` - `"com.widevine.alpha"` ウィデビンにとって

* `licenseServerURL`  — ライセンス要求を受け取る Widevine ライセンスサーバーの URL。
* `requestProperties`  — 送信ライセンス要求に含める追加のヘッダーが含まれます。

例えば、Expressplay DRM 用にパッケージ化されたコンテンツを使用する場合は、再生の前に次のコードを使用します。

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```
