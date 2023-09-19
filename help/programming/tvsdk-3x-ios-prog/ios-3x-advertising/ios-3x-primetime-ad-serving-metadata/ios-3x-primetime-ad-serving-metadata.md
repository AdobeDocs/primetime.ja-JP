---
description: TVSDK は、VOD およびライブ/リニアストリームの広告の解決と挿入をサポートします。
title: Primetime 広告サーバーメタデータ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 概要 {#primetime-ad-server-metadata-overview}

TVSDK は、VOD およびライブ/リニアストリームの広告の解決と挿入をサポートします。

## 前提条件

ビデオコンテンツに広告を含める前に、次のメタデータ情報を提供します。

* A `mediaID`：再生する特定のコンテンツを識別します。
* お使いの `zoneID`：会社または Web サイトを識別します。
* 広告サーバードメイン。割り当てられた広告サーバーのドメインを指定します。
* その他のターゲティングパラメーター。

## Primetime 広告サーバーメタデータの設定 {#section_86C4A3B2DF124770B9B7FD2511394313}

アプリケーションは、必要なを TVSDK に提供する必要があります `PTAuditudeMetadata` 広告サーバーに接続する情報。

広告サーバーのメタデータを設定するには：

1. のインスタンスを作成 [PTAuditudeMetadata](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAuditudeMetadata.html) プロパティを設定します。

   ```
   PTAuditudeMetadata *adMetadata = [[PTAuditudeMetadata alloc] init];  
   adMetadata.zoneId = @"INSERT_YOUR_ZONE_ID_HERE"; 
   adMetadata.domain = @"INSERT_YOUR_DOMAIN_HERE"; 
   // Optionally set user agent 
   adMetadata.userAgent = @"INSERT_AGENT_NAME_HERE; 
   ```

1. を設定します。 `PTAuditudeMetadata` 現在ののメタデータとしてのインスタンス `PTMediaPlayerItem` 使用するメタデータ `PTAdResolvingMetadataKey`.

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
