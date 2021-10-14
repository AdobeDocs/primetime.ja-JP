---
description: プレーヤーを設定して、ビデオの使用状況を追跡および分析できます。
title: ビデオ分析の初期化と設定
exl-id: dbb1e0b4-2a9e-4687-952d-4772440c1643
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# ビデオ分析の初期化と設定{#initialize-and-configure-video-analytics}

プレーヤーを設定して、ビデオの使用状況を追跡および分析できます。

ビデオトラッキング（ビデオハートビート）をアクティブ化する前に、以下があることを確認します。

* iOS向け TVSDK
* 設定/初期化情報 — 特定のビデオトラッキングアカウント情報については、Adobe担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>重要： この JSON 設定ファイル名は、 <span class="codeph"> ADBMobileConfig.json </span> のままにしておく必要があります。 この構成ファイルの名前とパスは変更できません。 このファイルのパスは <span class="codeph"> &lt;source root&gt;/AdobeMobile </span> にする必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AppMeasurement トラッキング </span> サーバーエンドポイント </td> 
   <td colname="col2"> Adobe Analytics( 旧称、SiteCatalyst) のバックエンド収集エンドポイントの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ビデオ分析トラッキングサーバーエンドポイント </td> 
   <td colname="col2"> ビデオ分析のバックエンド収集エンドポイントの URL。 すべてのビデオハートビートトラッキングコールが送信される場所です。 <p>ヒント： 訪問者トラッキングサーバーの URL は、Analytics トラッキングサーバーの URL と同じです。 訪問者 ID サービスの実装について詳しくは、 <a href="https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en" format="html" scope="external"> ID サービスの実装 </a> を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アカウント名 </td> 
   <td colname="col2"> レポートスイート ID(RSID) とも呼ばれます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marketing Cloud組織 ID </td> 
   <td colname="col2"> 訪問者コンポーネントのインスタンス化に必要な文字列値。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 発行者 </td> 
   <td colname="col2"> これは Publisher ID で、Adobe担当者から顧客に提供されます。 <p>ヒント： この ID は、単なるブランド名/テレビ名の文字列ではありません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

プレーヤーでビデオトラッキングを設定するには：

1. `ADBMobileConfig.json` リソースファイルの読み込み時間オプションが正しいことを確認します。

   ```
   { 
       "version" : "1.1", 
       "analytics" : { 
           "rsids" : "adobedevelopment", 
           "server" : "10.131.129.149:3000", 
           "charset" : "UTF-8", 
           "ssl" : false, 
           "offlineEnabled" : false, 
           "lifecycleTimeout" : 5, 
           "batchLimit" : 50, 
           "privacyDefault" : "optedin", 
           "poi" : [] 
       }, 
       "marketingCloud": { 
           "org": "ADOBE PROVIDED VALUE"  
       }, 
       "target" : { 
           "clientCode" : "", 
           "timeout" : 5 
       }, 
       "audienceManager" : { 
           "server" : "" 
       } 
   }
   ```

   この JSON 形式の設定ファイルは、TVSDK にリソースとしてバンドルされています。 プレーヤーは読み込み時にのみこれらの値を読み取り、アプリケーションの実行中は値は一定に保たれます。

   読み込み時間オプションを設定するには：

   1. `ADBMobileConfig.json` ファイルに、Adobeで指定された適切な値が含まれていることを確認します。
   1. このファイルが `AdobeMobile` フォルダー内にあることを確認します。

      このフォルダーは、アプリケーションソースツリーのルートに存在する必要があります。
   1. アプリケーションをコンパイルしてビルドします。
   1. バンドルされたアプリケーションをデプロイして実行します。

      これらの AppMeasurement 設定について詳しくは、[Adobe Analyticsでのビデオの測定 ](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=en) を参照してください。
1. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化できます。 モジュールを再初期化する前に、ビデオ分析メタデータも正しいコンテンツメタデータに更新されていることを確認します。 メタデータを再作成するには、手順 1 と 2 を繰り返します。

   1. ビデオ分析メタデータのインスタンスを作成します。

      このインスタンスには、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報が含まれています。 例：

      ```
      - (PTVideoAnalyticsTrackingMetadata *)getVideoAnalyticsTrackingMetadata 
      { 
          PTVideoAnalyticsTrackingMetadata *vaTrackingMetadata =  
            [[[PTVideoAnalyticsTrackingMetadata alloc]  
                 initWithTrackingServer:@"example.com" 
                 publisher:@"sample-publisher"] autorelease]; 
      
          // Set these to NO for production deployment. 
          vaTrackingMetadata.debugLogging = YES;  
          vaTrackingMetadata.quietMode = NO; 
      
          vaTrackingMetadata.channel = @"test-channel"; 
          vaTrackingMetadata.videoName = @"myvideo"; 
          vaTrackingMetadata.videoId = @"myvideoid"; 
          vaTrackingMetadata.playerName = @"PSDK Player"; 
          vaTrackingMetadata.enableChapterTracking = YES; 
          vaTrackingMetadata.useSSL = NO; 
          // use this API to override the default asset length -1 for live streams 
          vaTrackingMetadata.assetDuration = SAMPLE_ASSET_DURATION; 
      
      }
      ```

   1. ビデオ分析メタデータをグローバルメタデータインスタンスに追加します。

      準備が整ったら、メディアリソースまたはメディアプレーヤーアイテムにグローバルメタデータインスタンスを設定します。

      ```
      - (PTMetadata *)createMetadata 
      { 
          PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
      
          [metadata setMetadata:[self getVideoAnalyticsTrackingMetadata]  
            forKey:PTVideoAnalyticsTrackingMetadataKey]; 
      
          return metadata; 
      } 
      
      PTMetadata *metadata = [self createMetadata]; 
      
      PTMediaPlayerItem *item =  
        [[[PTMediaPlayerItem alloc] initWithUrl:[[[NSURL alloc]  
          initWithString:@"media-url"] autorelease] 
          mediaId:@"media-id" metadata:metadata] autorelease];
      ```

   1. ビデオ分析トラッカーを初期化します。

      メディアプレーヤーインスタンスを作成した後、ビデオ分析トラッカーインスタンスを作成し、メディアプレーヤーインスタンスへの参照を指定する必要があります。

      >[!TIP]
      >
      >コンテンツ再生セッションごとに新しいトラッカーインスタンスを作成し、メディアプレーヤーインスタンスを分離した後で、以前の参照を必ず削除してください。

      ```
      self.videoAnalyticsTracker =  
        [[[PTVideoAnalyticsTracker alloc] initWithMediaPlayer:self.player] autorelease];
      ```

   1. ビデオ分析トラッカーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、ビデオトラッカーインスタンスを破棄するまで数分待ちます。 インスタンスを直ちに破棄すると、ビデオ分析トラッカーがビデオ完了 ping を送信する機能を妨げる可能性があります。

      ```
      self.videoAnalyticsTracker = nil;
      ```

   1. ライブ/リニアストリームを手動で完了とマークします。

      1 つのライブストリームに様々なエピソードがある場合、完全な API を使用して、エピソードを手動で完了とマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >この API はオプションで、VOD ビデオトラッキングには不要です。

      ```
      if (self.videoAnalyticsTracker) 
      { 
         [self.videoAnalyticsTracker trackVideoComplete];   
      }
      ```
