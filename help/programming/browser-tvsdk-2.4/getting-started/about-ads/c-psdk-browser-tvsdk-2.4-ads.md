---
description: コンテンツの再生中に、Browser TVSDKは、MediaResourceオブジェクトの作成時に広告を表示し、広告に関する情報を渡すことができます。
seo-description: コンテンツの再生中に、Browser TVSDKは、MediaResourceオブジェクトの作成時に広告を表示し、広告に関する情報を渡すことができます。
seo-title: 広告
title: 広告
uuid: 9a5e8c83-18ce-41e8-9cb1-fdc9da903faf
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 概要 {#ads-overview}

コンテンツの再生中に、Browser TVSDKは、MediaResourceオブジェクトの作成時に広告を表示し、広告に関する情報を渡すことができます。

オプションで、受信後に関 `prepareToPlay` 数を呼び出すことができま `AdobePSDK.MediaPlayerStatus.INITIALIZED`す。

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

ブラウザーTVSDKは、広告の再生中にコンテンツが早送りされないようにするために、イベントハンドラーで使用できる次の広告固有のイベントも提供します。

* `AdobePSDK.PSDKEventType.AD_BREAK_STARTED`
* `AdobePSDK.PSDKEventType.AD_BREAK_COMPLETED`
* `AdobePSDK.PSDKEventType.AD_STARTED`
* `AdobePSDK.PSDKEventType.AD_COMPLETED`

この機能をUIフレームワークで表示するには、次のように設定で広告設定を指定します。

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

必要な情報について詳しくは、広告挿入メ `AuditudeSettings`タデータを参 [照してください](../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md)。
