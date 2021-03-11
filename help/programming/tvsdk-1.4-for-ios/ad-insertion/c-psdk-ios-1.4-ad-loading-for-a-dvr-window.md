---
description: ユーザーの現在のライブポイントより後に発生する広告のみを解決するか、現在のライブポイントより前に発生する広告も解決するかを決定できます。
title: DVR時間に対する広告の読み込み
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# DVR時間に対する広告の読み込み{#load-ad-for-a-dvr-window}

ユーザーの現在のライブポイントより後に発生する広告のみを解決するか、現在のライブポイントより前に発生する広告も解決するかを決定できます。

ユーザーがDVRストリームの開始時に表示コンテンツに開始した場合、TVSDKは、その時点でストリームのすべての広告を解決します。 ただし、ユーザーがストリームの開始後の時点で表示コンテンツに開始した場合、ユーザーの現在のライブポイントより後の広告のみを解決するか、現在のライブポイントより前の広告も解決するかを決定できます。

>[!TIP]
>
>現在のライブポイントより後の広告の解決は高速ですが、ユーザーが後ろにシークすると、以前に表示された広告は再生されなくなります。

## DVR時間{#section_2D93E2E947644D66B6F6ED1DD6742C25}の広告読み込みを制御

DVR時間に対する広告の読み込みを制御するには：

ストリーム全体の広告をすべて読み込むには、`PTAdMetadata.enableDVRAds`プロパティを`YES`に設定します。

>[!NOTE]
>
>デフォルト値は`NO`で、このオプションは現在のライブポイントからの広告のみを読み込みます。

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
