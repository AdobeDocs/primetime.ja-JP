---
description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
seo-description: TVSDKは、VODおよびライブ/リニアストリームの広告の解決と挿入をサポートしています。
seo-title: Primetime広告サーバーメタデータ
title: Primetime広告サーバーメタデータ
uuid: 61e224dd-551a-438f-8560-e64915087fef
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# フルイベント再生での広告の有効化 {#section_6016E1DAF03645C8A8388D03C6AB7571}

フルイベント再生(FER)は、ライブ/DVRアセットとして機能するVODアセットなので、広告が正しく配置されるように、アプリケーションで手順を実行する必要があります。

ライブコンテンツの場合、TVSDKは、マニフェスト内のメタデータ/キューを使用して、広告を配置する場所を決定します。 ただし、ライブ/リニアコンテンツは、VODコンテンツに似ている場合があります。 例えば、ライブコンテンツが完了すると、ラ `EXT-X-ENDLIST` イブマニフェストにタグが追加されます。 HLSの場合、タグは、ス `EXT-X-ENDLIST` トリームがVODストリームであることを意味します。 TVSDKは、広告を正しく挿入するために、このストリームを通常のVODストリームと自動的に区別することはできません。

アプリケーションは、コンテンツがライブかVODかをTVSDKに通知する必要があります。そのためには、 `PTAdSignalingMode`

FERストリームの場合、再生を開始する前にタイムラインに挿入する必要がある広告の時間のリストは、Adobe Primetime ad decisioningサーバーで提供されません。 これは、VODコンテンツの一般的なプロセスです。 代わりに、別のシグナリングモードを指定することで、TVSDKはFERマニフェストからすべてのキューポイントを読み取り、各キューポイントの広告サーバーに移動して広告の時間をリクエストします。 このプロセスは、ライブ/DVRコンテンツに似ています。

キューポイントに関連付けられた各リクエストに加えて、TVSDKは、プリロール広告に対して追加の広告リクエストを作成します。

1. vCMSなどの外部ソースから、使用するシグナリングモードを取得します。
1. 広告関連のメタデータを作成します。
1. デフォルトの動作を上書きする必要がある場合は、を使用して `PTAdSignalingMode` を指定しま `PTAdMetadata.signalingMode`す。

   有効な値は、、 `PTAdSignalingModeDefault`およ `PTAdSignalingModeManifestCues`びです `PTAdSignalingModeServerMap`。

   呼び出す前に、広告シグナリングモードを設定する必要がありま `prepareToPlay`す。 TVSDKが広告の解決を開始し、広告をタイムラインに配置した後、広告シグナリングモードに対する変更は無視されます。 リソースの広告メタデータを作成する際に、モードを設定します。

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
