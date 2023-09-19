---
description: コンテンツの再生中に、Browser TVSDK は、MediaResource オブジェクトの作成時に広告を表示し、広告に関する情報を渡すことができます。
title: 広告
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# 概要 {#ads-overview}

コンテンツの再生中に、Browser TVSDK は、MediaResource オブジェクトの作成時に広告を表示し、広告に関する情報を渡すことができます。

必要に応じて、 `prepareToPlay` 受け取った後の関数 `AdobePSDK.MediaPlayerStatus.INITIALIZED`.

```js
function onStatusChange (event) { 
   switch (event.status) { 
     case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
        player.prepareToPlay(AdobePSDK.MediaPlayer.LIVE_POINT); 
        break; 
     case AdobePSDK.MediaPlayerStatus.PREPARED: 
        player.play(); 
        break; 
   } 
} 
 
var auditudeSettings     = new AdobePSDK.AuditudeSettings(); 
auditudeSettings.domain  = "sample_auditude_domain"; 
auditudeSettings.mediaId = "sample_media_id"; 
auditudeSettings.zoneId  = "sample_zone_id"; 
 
// event handler 
player.addEventListener(AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange); 
 
var mediaResource = new AdobePSDK.MediaResource(resourceUrl, resourceType, auditudeSettings, false);
```

また、ブラウザー TVSDK は、広告の再生中にコンテンツが高速転送されるのを防ぐために、イベントハンドラーで使用できる以下の広告固有のイベントも提供します。

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`
* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

これを UI フレームワークで表示するには、次のように、設定で広告設定を指定します。

```js
// Using UI Framework 
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
    player: { 
        mediaResource: { 
 
            resourceUrl:'Specify Resource Url', 
 
            auditudeSettings: { 
                validMimeTypes: ["application/x-mpeURL"], 
                domain: "Sample_auditude_domain", 
                mediaId:"sample_media_id", 
                zoneID:"sample_zone_id", 
                creativeRepackagingEnabled:true 
            } 
        } 
    } 
}; 
```

必要な `AuditudeSettings`を参照してください。 [広告挿入メタデータ](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md).
