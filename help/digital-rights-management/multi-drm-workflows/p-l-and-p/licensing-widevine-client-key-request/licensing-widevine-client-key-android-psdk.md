---
description: クライアントコードはデータを Android API に渡します。
title: Android PSDK でのキーリクエストワークフロー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Android PSDK でのキーリクエストワークフロー{#key-request-workflow-on-android-psdk}

クライアントコードはデータを Android API に渡します。

Android では、クライアントコードは、次の API を使用して、ライセンスサーバー URL と付属のライセンス取得データを渡す必要があります。

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

この API が正常に呼び出された後、コードは通常の方法でコンテンツの再生を開始できます。 ExpressPlay を使用している場合は、トークンをライセンスサーバー URL の一部として渡すか、リクエストプロパティとして渡して、ライセンスサーバー URL からトークンを取り除くことができます。

一部の Android デバイスは、Widevine と PlayReady の両方をサポートしています。 そのようなデバイスでは、コンテンツに複数の DRM ヘッダーがある場合、顧客は特定の DRM を使用して PSDK でコンテンツを復号化するよう強制することができます。 これは、再生前に次の API を呼び出すことで実行できます。

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
