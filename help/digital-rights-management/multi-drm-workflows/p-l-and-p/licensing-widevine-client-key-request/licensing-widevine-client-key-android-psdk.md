---
description: クライアントコードは、Android APIにデータを渡します。
title: Android PSDKのキーリクエストワークフロー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Android PSDK{#key-request-workflow-on-android-psdk}のキーリクエストワークフロー

クライアントコードは、Android APIにデータを渡します。

Androidでは、次のAPIを使用して、クライアントコードにライセンスサーバーのURLとそれに付随するライセンス取得データを渡す必要があります。

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

このAPIの呼び出しが完了すると、コードは通常の方法で開始コンテンツを再生できます。 Expressplayを使用している場合は、トークンをライセンスサーバーURLの一部として渡すか、リクエストプロパティとして渡して、ライセンスサーバーURLからトークンを取り除くことができます。

一部のAndroidデバイスは、WidevineとPlayReadyの両方をサポートしています。 このようなデバイスでは、コンテンツに複数のDRMヘッダーがある場合、顧客は特定のDRMを使用してPSDKにコンテンツの復号化を強制する必要があります。 これは、再生前に次のAPIを呼び出すことで実行できます。

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

