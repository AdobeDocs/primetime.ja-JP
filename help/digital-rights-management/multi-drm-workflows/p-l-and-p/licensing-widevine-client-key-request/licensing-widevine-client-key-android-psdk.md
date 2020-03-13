---
description: クライアントコードは、Android APIにデータを渡します。
seo-description: クライアントコードは、Android APIにデータを渡します。
seo-title: Android PSDKのキーリクエストワークフロー
title: Android PSDKのキーリクエストワークフロー
uuid: 575163de-0f96-434d-a3ff-7e114caf72de
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Android PSDKのキーリクエストワークフロー{#key-request-workflow-on-android-psdk}

クライアントコードは、Android APIにデータを渡します。

Androidでは、次のAPIを使用して、クライアントコードがライセンスサーバーのURLと付随するライセンス取得データを渡す必要があります。

```
class DRMManager 
   { 
   ... 
   /* 
   * Set the license server URL and attached request properties that the PSDK should use for the passed in drm type.  
   * 
   * drmType: "com.widevine.alpha" for widevine. "com.microsoft.playready" for playready. 
   * licenseServerURL: self explanatory.  
   * requestProperties: key value pairs to be attached as HTTP headers to all license request sent to the passed in license server URL. Pass in 
   * NULL if none is needed.  
   */ 
   public static void setProtectionData(String drmType, String licenseServerURL,  Map<String, String> requestProperties); 
    }
```

このAPIが正常に呼び出された後、コードは通常の方法でコンテンツの再生を開始できます。 Expressplayを使用している場合は、トークンをライセンスサーバーのURLの一部として渡すか、リクエストプロパティとして渡し、ライセンスサーバーのURLからトークンを取り除くことができます。

一部のAndroidデバイスは、WidevineとPlayReadyの両方をサポートしています。 このようなデバイスでは、コンテンツに複数のDRMヘッダーが含まれる場合、顧客は特定のDRMを使用してPSDKに強制的にコンテンツの復号化を行わせる必要があります。 これは、再生前に次のAPIを呼び出すことで実行できます。

```
class MediaPlayer 
   { 
   ... 
    
   /* 
   * drm: pass in "com.widevine.alpha" for widevine or "com.microsoft.playready" for playready 
   * 
   */ 
   public void setDRMScheme(String drm) throws MediaPlayerException 
   }
```

