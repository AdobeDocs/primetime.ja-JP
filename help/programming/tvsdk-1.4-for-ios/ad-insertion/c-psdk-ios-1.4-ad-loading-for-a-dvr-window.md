---
description: ユーザーの現在のライブポイントの後に発生する広告のみを解決するか、現在のライブポイントの前に発生する広告も解決するかを決定できます。
seo-description: ユーザーの現在のライブポイントの後に発生する広告のみを解決するか、現在のライブポイントの前に発生する広告も解決するかを決定できます。
seo-title: DVR時間の広告の読み込み
title: DVR時間の広告の読み込み
uuid: 67bc3924-3d17-4d1a-b9a7-be8d0488a970
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# DVR時間の広告の読み込み {#load-ad-for-a-dvr-window}

ユーザーの現在のライブポイントの後に発生する広告のみを解決するか、現在のライブポイントの前に発生する広告も解決するかを決定できます。

ユーザーがDVRストリームの開始時にコンテンツの表示を開始すると、TVSDKは、その時点でストリームのすべての広告を解決します。 ただし、ユーザーがストリームの開始後の時点でコンテンツの表示を開始した場合は、ユーザーの現在のライブポイントの後に発生した広告のみを解決するか、現在のライブポイントの前に発生した広告も解決するかを決定できます。

>[!TIP]
>
>現在のライブポイント後の広告の解決は高速ですが、ユーザーが後方にシークした場合、このオプションを選択すると、以前に表示された広告は再生されません。

## DVR時間の広告読み込みの制御 {#section_2D93E2E947644D66B6F6ED1DD6742C25}

DVR時間の広告の読み込みを制御するには：

ストリーム全体のすべての広告を読み込むには、このプロパティをに `PTAdMetadata.enableDVRAds` 設定しま `YES`す。

>[!NOTE]
>
>デフォルト値はです。こ `NO`のオプションは、現在のライブポイントからの広告のみを読み込みます。

例：

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
 
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
adMetadata.zoneId = <ZoneId>; 
adMetadata.domain = <Domain>; 
 
// Enable DVR Ads by setting to YES the enableDVRAds property on PTAdMetadata  
// (PTAuditudeMetadata is a subclass of PTAdMetadata)  
adMetadata.enableDVRAds = YES; 
 
[metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
 
//Create PTMediaPlayerItem with the previously prepared metadata    
playerItem = [[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata]; 
```
