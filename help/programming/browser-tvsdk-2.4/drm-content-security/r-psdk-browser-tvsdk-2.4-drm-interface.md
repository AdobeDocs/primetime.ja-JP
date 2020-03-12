---
description: ブラウザーTVSDKは、FairPlay、PlayReady、Widevineなど、様々なDRMソリューションで保護されたコンテンツを再生するためのDRMインターフェイスを提供します。
seo-description: ブラウザーTVSDKは、FairPlay、PlayReady、Widevineなど、様々なDRMソリューションで保護されたコンテンツを再生するためのDRMインターフェイスを提供します。
seo-title: DRMインターフェイスの概要
title: DRMインターフェイスの概要
uuid: b553ebad-8310-4517-8d97-ef8a1c5f4340
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# DRMインターフェイスの概要{#drm-interface-overview}

ブラウザーTVSDKは、FairPlay、PlayReady、Widevineなど、様々なDRMソリューションで保護されたコンテンツを再生するためのDRMインターフェイスを提供します。

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRMは、Microsoft PlayReady（Windows 8.1およびEdgeのInternet Explorer）およびWidevine（Google Chromeの）DRMシステムで保護されたMPEG-Dashストリームで使用できます。 FairPlayで保護されたSafari上のHLSストリームに対してDRMサポートを利用できます。

DRMワークフローの主要なインターフェイスは、です `DRMManager`。 インスタンスへの参 `DRMManager` 照は、MediaPlayerインスタンスを通じて取得できます。

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

DRM保護されたコンテンツを再生するための高度なワークフローを次に示します。

1. 保護されたストリームのライセンス取得プロセスでブラウザーTVSDKが使用するDRMシステム固有のデータを添付するには、呼び出す前に次の呼び出しを行いま `mediaPlayer.replaceCurrentResource`す。

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

1. 保護データが設定されていない場合、必要な情報（ライセンスURLなど）は、該当するDRMシステムのPSSHボックスから取得されます。

   >[!TIP]
   >
   >保護データを指定すると、「PSSH」ボックスで指定されたライセンスURLが上書きされます。

1. デフォルトでは、DRMライセンスのセッションタイプは一時的で、セッションが閉じた後はライセンスは保存されません。

   のAPIを使用して、セッションタイプを指定できま `DRMManager`す。  後方互換性を保つため、、、およびのセッ `temporary`ションタ `persistent-license`イプを `persistent-usage-record`使用できま `persistent`す。

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. がまたはの場 `sessionType` 合、を呼 `persistent-license` び出すこ `persistent`とでDRMライセンスを返すことができま `DRMManager.returnLicense`す。

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

