---
description: TVSDK は、VOD およびライブ/リニアストリームの広告の解決と挿入をサポートします。
title: Primetime 広告サーバーメタデータ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# 概要 {#primetime-ad-server-metadata-overview}

TVSDK は、VOD およびライブ/リニアストリームの広告の解決と挿入をサポートします。

>[!NOTE]
>
>ビデオコンテンツに広告を含める前に、次のメタデータ情報を提供します。
>
>* A `mediaID`：再生する特定のコンテンツを識別します。
>* お使いの `zoneID`：会社または Web サイトを識別します。
>* 広告サーバードメイン。割り当てられた広告サーバーのドメインを指定します。
>* その他のターゲティングパラメーター。
>

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

## フルイベント再生での広告の有効化 {#section_6016E1DAF03645C8A8388D03C6AB7571}

フルイベント再生 (FER) は、ライブ/DVR アセットとして機能する VOD アセットなので、広告が正しく配置されるように、アプリケーションが手順を実行する必要があります。

ライブコンテンツの場合、 TVSDK はマニフェスト内のメタデータ/キューを使用して、広告を配置する場所を決定します。 ただし、ライブ/リニアコンテンツは、VOD コンテンツに似ている場合があります。 例えば、ライブコンテンツが完了すると、 `EXT-X-ENDLIST` タグがライブマニフェストに追加されます。 HLS の場合、 `EXT-X-ENDLIST` タグは、ストリームが VOD ストリームであることを意味します。 TVSDK は、広告を正しく挿入するために、このストリームを通常の VOD ストリームと自動的に区別することはできません。

コンテンツがライブか VOD かを TVSDK に知らせるには、 `PTAdSignalingMode`.

FER ストリームの場合、Adobe Primetime Ad Decisioning サーバーは、再生を開始する前にタイムラインに挿入する必要がある広告の時間のリストを提供しないでください。 これは、VOD コンテンツの一般的な手順です。 代わりに、異なるシグナリングモードを指定することで、 TVSDK は FER マニフェストからすべてのキューポイントを読み取り、各キューポイントの広告サーバーに移動して広告ブレークをリクエストします。 このプロセスは、ライブ/DVR コンテンツに似ています。

TVSDK は、キューポイントに関連付けられた各リクエストに加えて、プリロール広告に対する追加の広告リクエストを作成します。

1. vCMS などの外部ソースから、使用するシグナリングモードを取得します。
1. 広告関連のメタデータを作成します。
1. デフォルトの動作を上書きする必要がある場合は、 `PTAdSignalingMode` 使用によって `PTAdMetadata.signalingMode`.

   有効な値は次のとおりです。 `PTAdSignalingModeDefault`, `PTAdSignalingModeManifestCues`、および `PTAdSignalingModeServerMap`.

   を呼び出す前に、広告シグナリングモードを設定する必要があります `prepareToPlay`. TVSDK が広告の解決を開始し、広告をタイムラインに配置し始めると、広告シグナリングモードへの変更は無視されます。 リソースの広告メタデータを作成する際に、モードを設定します。

1. 再生を続行します。

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
