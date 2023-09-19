---
description: ユーザーの現在のライブポイントの後に発生する広告のみを解決するか、現在のライブポイントの前に発生する広告も解決するかを決定できます。
title: DVR 時間枠の広告を読み込む
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# DVR 時間枠の広告を読み込む {#load-ad-for-a-dvr-window}

ユーザーの現在のライブポイントの後に発生する広告のみを解決するか、現在のライブポイントの前に発生する広告も解決するかを決定できます。

ユーザーが DVR ストリームの開始時にコンテンツの表示を開始すると、 TVSDK はその時点でそのストリームのすべての広告を解決します。 ただし、ユーザーがストリームの開始後の時点でコンテンツの表示を開始する場合、ユーザーの現在のライブポイントの後に発生した広告のみを解決するか、現在のライブポイントの前に発生した広告も解決するかを決定できます。

>[!TIP]
>
>現在のライブポイント以降の広告の解決はより高速ですが、ユーザーが後方にシークした場合、このオプションは、以前に表示された広告の再生を妨げます。

## DVR 時間枠の広告読み込みの制御 {#section_2D93E2E947644D66B6F6ED1DD6742C25}

DVR ウィンドウの広告読み込みを制御するには：

ストリーム全体のすべての広告を読み込むには、 `PTAdMetadata.enableDVRAds` プロパティを `YES`.

>[!NOTE]
>
>デフォルト値は `NO`を指定し、現在のライブポイントからのみ広告を読み込みます。

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
