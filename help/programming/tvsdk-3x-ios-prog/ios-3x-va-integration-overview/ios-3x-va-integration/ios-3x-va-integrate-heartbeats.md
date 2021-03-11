---
description: ビデオの使用を追跡および分析するようにプレイヤーを設定できます。
title: ビデオ分析の初期化と設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# ビデオ分析の初期化と設定{#initialize-and-configure-video-analytics}

ビデオの使用を追跡および分析するようにプレイヤーを設定できます。

ビデオトラッキング（ビデオハートビート）をアクティブ化する前に、以下があることを確認します。

* TVSDK for iOS
* 設定/初期化情報 — 特定のビデオ追跡アカウント情報については、Adobeの担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>重要： このJSON設定ファイル名は<span class="codeph"> ADBMobileConfig.json </span>のままにしておく必要があります。 この構成ファイルの名前とパスは変更できません。 このファイルへのパスは、<span class="codeph"> &lt;source root&gt;/AdobeMobile </span>でなければなりません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AppMeasurement </span> トラッキングサーバーエンドポイント </td> 
   <td colname="col2"> Adobe Analytics(旧称SiteCatalyst)のバックエンド収集エンドポイントのURLです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ビデオ分析トラッキングサーバーエンドポイント </td> 
   <td colname="col2"> Video Analyticsのバックエンド収集エンドポイントのURL。 すべてのビデオハートビートトラッキング呼び出しが送信される場所です。 <p>ヒント： 訪問者トラッキングサーバーのURLは、AnalyticsトラッキングサーバーのURLと同じです。 訪問者IDサービスの実装について詳しくは、<a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external">実装IDサービス</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アカウント名 </td> 
   <td colname="col2"> レポートスイートID(RSID)とも呼ばれます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marketing Cloud組織ID </td> 
   <td colname="col2"> 訪問者コンポーネントのインスタンス化に必要なstring値。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 投稿者 </td> 
   <td colname="col2"> これはPublisher IDで、Adobeの担当者からお客様に提供されます。 <p>ヒント： このIDは、単なるブランド名やテレビ名を持つ文字列ではありません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

プレーヤーでビデオトラッキングを設定するには：

1. `ADBMobileConfig.json`リソースファイルの読み込み時間オプションが正しいことを確認します。

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

   このJSON形式の設定ファイルは、TVSDKにリソースとしてバンドルされています。 プレイヤーは、読み込み時にのみこれらの値を読み取り、アプリケーションの実行中、値は一定のままです。

   読み込み時間オプションを設定するには：

   1. `ADBMobileConfig.json`ファイルに、Adobeが提供する適切な値が含まれていることを確認します。
   1. このファイルが`AdobeMobile`フォルダー内にあることを確認します。

      このフォルダーは、アプリケーションソースツリーのルートに存在する必要があります。
   1. アプリケーションをコンパイルしてビルドします。
   1. バンドルされたアプリケーションをデプロイして実行します。

      これらのAppMeasurement設定について詳しくは、[Adobe Analyticsでのビデオの測定](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/)を参照してください。
1. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化できます。 モジュールを再初期化する前に、ビデオ分析メタデータも正しいコンテンツメタデータに更新されていることを確認します。 メタデータを再作成するには、手順1と2を繰り返します。

   1. ビデオ分析メタデータのインスタンスを作成します。

      このインスタンスは、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報を含みます。 例：

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

   1. グローバルメタデ追加ータインスタンスに対するVideo Analyticsメタデータ。

      準備が整ったら、メディアリソースまたはメディアプレイヤー項目にグローバルメタデータインスタンスを設定します。

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

      メディアプレイヤーインスタンスを作成した後、ビデオ分析トラッカーインスタンスを作成し、メディアプレイヤーインスタンスの参照を指定する必要があります。

      >[!TIP]
      >
      >コンテンツ再生セッションごとに新しいトラッカーインスタンスを必ず作成し、メディアプレイヤーインスタンスをデタッチした後で、以前の参照を削除してください。

      ```
      self.videoAnalyticsTracker =  
        [[[PTVideoAnalyticsTracker alloc] initWithMediaPlayer:self.player] autorelease];
      ```

   1. ビデオ分析トラッカーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、ビデオトラッカーインスタンスを破棄するまで数分待ちます。 インスタンスをすぐに破棄すると、ビデオ分析トラッカーがビデオ完了pingを送信する機能を妨げる可能性があります。

      ```
      self.videoAnalyticsTracker = nil;
      ```

   1. 手動でライブ/リニアストリームを完了としてマークします。

      1つのライブストリームに様々なエピソードがある場合、完了APIを使用して、手動でエピソードを完了とマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >このAPIはオプションで、VODビデオトラッキングには必要ありません。

      ```
      if (self.videoAnalyticsTracker) 
      { 
         [self.videoAnalyticsTracker trackVideoComplete];   
      }
      ```
