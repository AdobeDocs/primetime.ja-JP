---
description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
seo-description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
seo-title: Primetime広告サーバーメタデータ
title: Primetime広告サーバーメタデータ
uuid: 314f14c0-4da4-4da6-96f9-5a5ffea22a99
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# 概要 {#primetime-ad-server-metadata-overview}

TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。

>[!NOTE]
>
>ビデオコンテンツに広告を含める前に、次のメタデータ情報を提供します。
>
>* 再生する特定 `mediaID`のコンテンツを識別する。
>* 会社 `zoneID`またはWebサイトを識別するユーザー。
>* 割り当てられた広告サーバーのドメインを指定する広告サーバードメイン。
>* その他のターゲティングパラメーター。

>



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

## フルイベント再生での広告の有効化 {#section_6016E1DAF03645C8A8388D03C6AB7571}

フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されていることを確認する手順をアプリケーションで実行する必要があります。

ライブコンテンツの場合、TVSDKは、マニフェスト内のメタデータ/キューを使用して、広告を配置する場所を決定します。 ただし、ライブ/リニアコンテンツは、VODコンテンツに似ている場合があります。 例えば、ライブコンテンツが完了すると、ライブマニフェストに `EXT-X-ENDLIST` タグが追加されます。 HLSの場合、 `EXT-X-ENDLIST` タグは、ストリームがVODストリームであることを意味します。 TVSDKは、広告を正しく挿入するために、このストリームを通常のVODストリームと自動的に区別することはできません。

アプリケーションで、コンテンツがライブかVODかをTVSDKに通知する必要があります。それには、 `PTAdSignalingMode`

FERストリームの場合、再生を開始する前にタイムラインに挿入する必要がある広告の時間のリストは、Adobe Primetimead decisioningサーバーで提供しないでください。 これは、VODコンテンツの一般的なプロセスです。 代わりに、別のシグナリングモードを指定することで、TVSDKは、FERマニフェストからすべてのキューポイントを読み取り、各キューポイントの広告サーバーに移動して広告の時間をリクエストします。 このプロセスは、ライブ/DVRコンテンツと似ています。

キューポイントに関連付けられている各リクエストに加えて、TVSDKは、プリロール広告に対して追加の広告リクエストを行います。

1. vCMSなどの外部ソースから、使用する必要があるシグナリングモードを取得します。
1. 広告関連のメタデータを作成します。
1. デフォルトの動作を上書きする必要がある場合は、を使用 `PTAdSignalingMode` してを指定し `PTAdMetadata.signalingMode`ます。

   有効な値は、 `PTAdSignalingModeDefault`、 `PTAdSignalingModeManifestCues`および `PTAdSignalingModeServerMap`です。

   呼び出す前に、広告シグナリングモードを設定する必要があり `prepareToPlay`ます。 TVSDK開始が広告を解決してタイムラインに配置した後、広告シグナリングモードに対する変更は無視されます。 広告シグナリングモードは、リソースの広告メタデータを作成するときに設定します。

1. 再生を続けます。

   ```
      PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.zoneId = your-auditude-zone-id; 
   adMetadata.domain = @"your-auditude-domain"; 
   //adMetadata.enableDVRAds = YES; // FOR LIVE DVR case 
   //adMetadata.signalingMode = PTAdSignalingModeManifestCues;  
   // FOR VOD FER case 
   NSMutableDictionary *targetingParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [targetingParameters setValue:@"ipad" forKey:@"device"]; 
   [targetingParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.targetingParameters = targetingParameters; 
   NSMutableDictionary *customParameters = [[[NSMutableDictionary alloc] init] autorelease]; 
   [customParameters setValue:@"your-media-id" forKey:@"NW_ID"]; 
   [customParameters setValue:@"preroll" forKey:@"AD_OPPORTUNITY_ID"]; 
   adMetadata.customParameters = customParameters; 
   [metadata setMetadata:adMetadata forKey:PTAdResolvingMetadataKey]; 
   ```

