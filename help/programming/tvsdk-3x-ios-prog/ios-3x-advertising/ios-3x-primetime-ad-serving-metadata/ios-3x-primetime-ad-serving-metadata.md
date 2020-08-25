---
description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
seo-description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
seo-title: Primetime広告サーバーメタデータ
title: Primetime広告サーバーメタデータ
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 9d60bff4035963572e49fa49effa576ca854f799
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# 概要 {#primetime-ad-server-metadata-overview}

TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。

## 前提条件

ビデオコンテンツに広告を含める前に、次のメタデータ情報を提供します。

* 再生する特定 `mediaID`のコンテンツを識別する。
* 会社 `zoneID`またはWebサイトを識別するユーザー。
* 割り当てられた広告サーバーのドメインを指定する広告サーバードメイン。
* その他のターゲティングパラメーター。

## Primetime広告サーバーメタデータの設定 {#section_86C4A3B2DF124770B9B7FD2511394313}

広告サーバーに接続するために必要な `PTAuditudeMetadata` 情報をTVSDKに提供する必要があります。

広告サーバーのメタデータを設定するには：

1. PTAuditudeMetadataのインスタンスを作成し [、そのプロパティを設定します](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) 。

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. を使用して、 `PTAuditudeMetadata` インスタンスを現在のメタデータのメタデータとして設定し `PTMediaPlayerItem` ま `PTAdResolvingMetadataKey`す。

   ```
   // Metadata is an instance of PTMetadata that is used to create the PTMediaPlayerItem 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey];  
   [adMetadata release];
   ```

   次に例を示します。

   ```
   PTMetadata *metadata = [self createMetadata]; 
   PTMediaPlayerItem *item =  
     [[[PTMediaPlayerItem alloc] initWithUrl:url mediaId:yourMediaID metadata:metadata] autorelease]; 
   
   - (PTMetadata *) createMetadata { 
       PTMetadata* metadata = [[[PTMetadata alloc] init] autorelease]; 
   
       PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease];  
       adMetadata.zoneId = yourZoneID; 
       adMetadata.domain = yourAdServerDomain; 
   
       [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   
       return metadata; 
   }
   ```
