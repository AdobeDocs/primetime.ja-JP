---
description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
title: Primetime広告サーバーメタデータ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# 概要{#primetime-ad-server-metadata-overview}

TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。

## 前提条件

ビデオコンテンツに広告を含める前に、次のメタデータ情報を提供します。

* 再生する特定のコンテンツを識別する`mediaID`。
* `zoneID`。会社またはWebサイトを識別します。
* 割り当てられた広告サーバーのドメインを指定する広告サーバードメイン。
* その他のターゲティングパラメーター。

## Primetime広告サーバーメタデータの設定{#section_86C4A3B2DF124770B9B7FD2511394313}

広告サーバーに接続するために必要な`PTAuditudeMetadata`情報をTVSDKに提供する必要があります。

広告サーバーのメタデータを設定するには：

1. [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html)のインスタンスを作成し、そのプロパティを設定します。

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. `PTAdResolvingMetadataKey`を使用して、`PTAuditudeMetadata`インスタンスを現在の`PTMediaPlayerItem`メタデータのメタデータとして設定します。

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
