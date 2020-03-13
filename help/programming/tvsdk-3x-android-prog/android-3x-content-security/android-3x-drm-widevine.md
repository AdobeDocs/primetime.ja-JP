---
description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションをアドビの統合ソリューションの代わりに使用することもできます。
seo-description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションをアドビの統合ソリューションの代わりに使用することもできます。
seo-title: Widevine DRM
title: Widevine DRM
uuid: 3a5fd786-4319-4e92-83b6-0f5328df6a44
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Widevine DRM {#widevine-drm}

Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションをアドビの統合ソリューションの代わりに使用することもできます。

サードパーティのDRMソリューションの可用性に関する最新情報については、アドビの担当者にお問い合わせください。

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

DASHストリームでは、AndroidネイティブWidevine DRMを使用できます。

再生を開始する前に、 `com.adobe.mediacore.drm.DRMManager` 次のAPIを呼び出します。

```java
public static void setProtectionData( 
    String drm,  
    String licenseServerURL,   
    Map<String, String> requestProperties)
```

引数：

* `drm`  — ウィデ `"com.widevine.alpha"` ビンに。

* `licenseServerURL`  — ライセンス要求を受け取るWidevineライセンスサーバーのURL。
* `requestProperties`  — 発信ライセンス要求に含める追加のヘッダーが含まれます。

例えば、Expressplay DRM用にパッケージ化されたコンテンツを使用する場合、再生する前に次のコードを使用します。

```java
DRMManager.setProtectionData( 
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null); 
```
