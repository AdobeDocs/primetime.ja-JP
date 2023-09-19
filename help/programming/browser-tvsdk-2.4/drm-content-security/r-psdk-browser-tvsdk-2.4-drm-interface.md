---
description: ブラウザー TVSDK は、FairPlay、PlayReady、Widevine など、様々な DRM ソリューションで保護されたコンテンツを再生するための DRM インターフェイスを提供します。
title: DRM インターフェイスの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# DRM インターフェイスの概要{#drm-interface-overview}

ブラウザー TVSDK は、FairPlay、PlayReady、Widevine など、様々な DRM ソリューションで保護されたコンテンツを再生するための DRM インターフェイスを提供します。

<!--<a id="section_59994F2059B245E996E0776214804A0A"></a>-->

>[!IMPORTANT]
>
>DRM は、Microsoft PlayReady（Windows 8.1 および Edge の Internet Explorer）および Widevine(Google Chrome の )DRM システムで保護された MPEG-Dash ストリームで使用できます。 Safari 上の HLS ストリームで FairPlay で保護されている DRM のサポートが利用できます。

DRM ワークフローの主なインターフェイスは、 `DRMManager`. への参照 `DRMManager` インスタンスは、 MediaPlayer インスタンスを通じて取得できます。

* `var mediaPlayer = new AdobePSDK.MediaPlayer();`
* `var drmManager = mediaPlayer.drmManager;`

<!--<a id="section_B7E8AD9A4D4F4BD9BA2A67ABC135D6F9"></a>-->

DRM で保護されたコンテンツを再生するための大まかなワークフローを次に示します。

1. 保護されたストリームのライセンス取得プロセスでブラウザー TVSDK が使用する DRM システム固有のデータを添付するには、呼び出す前に次の呼び出しをおこないます `mediaPlayer.replaceCurrentResource`:

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

1. 異なるブラウザーで異なる DRM システムで同じコンテンツが動作すると想定される場合、複数の DRM システムに対して保護データを指定できます。

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

1. 保護データが設定されていない場合、必要な情報（ライセンス URL など）は、DRM システム用の PSSH ボックスから取得されます（該当する場合）。

   >[!TIP]
   >
   >保護データを指定すると、PSSH ボックスで指定されたライセンス URL よりも優先されます。

1. デフォルトでは、DRM ライセンスのセッションタイプは一時的です。つまり、セッションが閉じられた後でライセンスが保存されないことを意味します。

   API を使用して、セッションのタイプを `DRMManager`.  下位互換性のために、セッションタイプには以下が含まれます。 `temporary`, `persistent-license`, `persistent-usage-record`、および `persistent`.

   ```js
   var drmManager = mediaPlayer.drmManager; 
    drmManager.setEMESessionType(“<YOUR_SESSION_TYPE>”); 
   ```

1. 次の場合に `sessionType` 使用済み `persistent-license` または `persistent`を呼び出すと、DRM ライセンスを返すことができます `DRMManager.returnLicense`.

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
