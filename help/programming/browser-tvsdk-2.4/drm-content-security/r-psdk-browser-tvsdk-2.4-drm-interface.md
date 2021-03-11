---
description: ブラウザーTVSDKは、FairPlay、PlayReady、Widevineなど、様々なDRMソリューションで保護されたコンテンツを再生するために使用できるDRMインターフェイスを提供します。
title: DRMインターフェイスの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# DRMインターフェイスの概要{#drm-interface-overview}

ブラウザーTVSDKは、FairPlay、PlayReady、Widevineなど、様々なDRMソリューションで保護されたコンテンツを再生するために使用できるDRMインターフェイスを提供します。

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRMサポートは、Microsoft PlayReady（Windows 8.1およびEdgeのInternet Explorer）およびWidevine（Google Chromeの）DRMシステムで保護されたMPEG-Dashストリームで利用できます。 Safari上のFairPlayで保護されたHLSストリームに対してDRMサポートを使用できます。

DRMワークフローの主なインターフェイスは`DRMManager`です。 `DRMManager`インスタンスへの参照は、MediaPlayerインスタンスを通じて取得できます。

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

DRM保護されたコンテンツを再生するための高レベルのワークフローを次に示します。

1. ブラウザーTVSDKが保護ストリームのライセンス取得プロセスで使用するDRMシステム固有のデータを添付するには、`mediaPlayer.replaceCurrentResource`を呼び出す前に次の呼び出しを行います。

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
          "serverURL": { 
             "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
             "license-request": "https://example.com:8096/flashaccess/req", 
             "license-release": "https://example.com:8096/flashaccess/req" 
          }, 
          "httpRequestHeaders": { 
          } 
       } 
   }; 
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. 同じコンテンツが異なるブラウザーの異なるDRMシステムで動作すると予想される場合、複数のDRMシステムに対して保護データを指定できます。

   ```js
   var protectionData = { 
       "com.adobe.primetime": { 
           "serverURL": { 
               "individualization-request": "https://individualization.adobe.com/flashaccess/i15n/v5", 
               "license-request": "https://example.com:8096/flashaccess/req", 
               "license-release": "https://example.com:8096/flashaccess/req" 
           }, 
           "httpRequestHeaders": { 
           } 
       }, 
       "com.widevine.alpha": { 
           "serverURL": "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "dt-custom-data": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.microsoft.playready": { 
           "serverURL": "https://pr.test.expressplay.com/playready/RightsManager.asmx?ExpressPlayToken=<token value>", 
           "httpRequestHeaders": { 
               "http-header-CustomData": "eyJ1c2VySWQiOiIxMjM0NS" 
           } 
       }, 
       "com.apple.fps.1_0": { 
           "serverURL": "https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<token value>", 
           "certificateURL": "Path_To_certificate.cer", 
           "licenseResponseType": "arraybuffer", 
           "httpRequestHeaders": { 
               "Content-type": "application/octet-stream" 
           } 
       }, 
       "org.w3.clearkey": { 
           "clearkeys": { 
               "H3JbV93QV3mPNBKQON2UtQ": "ClKhDPHMtCouEx1vLGsJsA", 
               "IAAAACAAIAAgACAAAAAAAg": "5t1CjnbMFURBou087OSj2w" 
           } 
       } 
   }; 
   
   var drmManager = mediaPlayer.drmManager; 
   drmManager.setProtectionData(protectionData);
   ```

1. 保護データが設定されていない場合、必要な情報（ライセンスURLなど）は、DRMシステムのPSSHボックスから取得されます（該当する場合）。

   >[!TIP]
   >
   >保護データを指定すると、「PSSH」ボックスで指定されたライセンスURLよりも優先されます。

1. デフォルトでは、DRMライセンスのセッションタイプは一時的です。つまり、セッションを閉じた後にライセンスは保存されません。

   `DRMManager`のAPIを使用して、セッションの種類を指定できます。  下位互換性を確保するため、セッションタイプには`temporary`、`persistent-license`、`persistent-usage-record`、`persistent`があります。

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. 使用する`sessionType`が`persistent-license`または`persistent`の場合、`DRMManager.returnLicense`を呼び出すことでDRMライセンスを返すことができます。

   ```js
   var onLicenseReturnFunc = function () { 
       console.log("DRM: License Return Complete "); 
   }, 
   
   onLicenseReturnErrorFunc = function (major, minor, errorString/*, errorServerUrl*/) { 
      console.log("DRM: License Return Error: " + errorString); 
   }, 
   
   drmManager = mediaPlayer.drmManager; 
   
   if (drmManager) { 
       var returnLicenseListener = new  
           AdobePSDK.DRMReturnLicenseListener(onLicenseReturnFunc, onLicenseReturnErrorFunc); 
       drmManager.returnLicense(null, null, null, false, returnLicenseListener, drmLicense.session); 
   }
   ```

