---
description: ビデオの使用を追跡および分析するようにプレーヤーを設定できます。
seo-description: ビデオの使用を追跡および分析するようにプレーヤーを設定できます。
seo-title: ビデオ分析の初期化と設定
title: ビデオ分析の初期化と設定
uuid: 262b1a28-2986-4fbb-a465-4ce8cefe18fb
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ビデオ分析の初期化と設定{#initialize-and-configure-video-analytics}

ビデオの使用を追跡および分析するようにプレーヤーを設定できます。

ビデオ追跡（ビデオハートビート）をアクティブ化する前に、次の事項を確認します。

* Android向けTVSDK
* 設定/初期化情報 — 特定のビデオトラッキングアカウント情報については、アドビの担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>重要： このJSON設定ファイル名は、ADBMobileConfig.jsonのま <span class="codeph"> まにする必要がありま </span>す。 この構成ファイルの名前とパスは変更できません。 このファイルへのパスは、 <span class="codeph"> &lt;source root&gt;/assetsである必要があります </span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AppMeasurementトラッキングサーバーエンドポイント </td> 
   <td colname="col2"> Adobe Analytics（旧称SiteCatalyst）のバックエンド収集エンドポイントのURL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ビデオ分析トラッキングサーバーエンドポイント </td> 
   <td colname="col2"> ビデオ分析のバックエンドコレクションエンドポイントのURLです。 これは、すべてのビデオハートビートトラッキング呼び出しが送信される場所です。 <p>ヒント： 訪問者トラッキングサーバーのURLは、AnalyticsトラッキングサーバーのURLと同じです。 訪問者IDサービスの実装について詳しくは、IDサービスの実装を <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> 参照してくださ </a>い。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アカウント名 </td> 
   <td colname="col2"> レポートスイートID(RSID)とも呼ばれます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marketing Cloud組織ID </td> 
   <td colname="col2"> 訪問者コンポーネントをインスタンス化するために必要なstring値。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 投稿者 </td> 
   <td colname="col2"> これはPublisher IDで、アドビの担当者が顧客に提供します。 <p>ヒント： このIDは、単なるブランド名やテレビ名を持つ文字列ではありません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

プレーヤーでビデオトラッキングを設定するには：

1. リソースファイルの読み込み時のオプションが正しい `ADBMobileConfig.json` ことを確認します。

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

   このJSON形式の設定ファイルは、TVSDKにリソースとしてバンドルされています。 プレイヤーは、読み込み時にのみこれらの値を読み取り、アプリケーションの実行中は値は一定のままです。

   読み込み時間オプションを設定するには：

   1. アドビが提供する `ADBMobileConfig.json` 適切な値がファイルに含まれていることを確認します。
   1. このファイルがフォルダー内にあることを確認 `assets` します。

      このフォルダーは、アプリケーションのソースツリーのルートに配置する必要があります。
   1. アプリケーションをコンパイルしてビルドします。
   1. バンドルされたアプリケーションをデプロイして実行します。

      これらのAppMeasurement設定について詳しくは、Adobe Analyticsでのビデオの測 [定を参照してください](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/)。
1. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化することができます。 モジュールを再初期化する前に、ビデオ分析のメタデータも正しいコンテンツのメタデータに更新されていることを確認します。 メタデータを再作成するには、手順1と2を繰り返します。

   1. ビデオ分析メタデータのインスタンスを作成します。

      このインスタンスには、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報が含まれています。 例：

      ```java
      private VideoAnalyticsMetadata getVideoAnalyticsTrackingMetadata() { 
          VideoAnalyticsMetadata vaMetadata = new VideoAnalyticsMetadata(); 
      
          vaMetadata.setTrackingServer("example.com"); 
          vaMetadata.setPublisher("sample-publisher"); 
          vaMetadata.setChannel("test-channel"); 
          vaMetadata.setVideoName("myvideo"); 
          vaMetadata.setVideoId("myvideoid"); 
          vaMetadata.setPlayerName("PSDK Player"); 
          vaMetadata.setUseSSL(false); 
          vaMetadata.debugLogging = true; // Set to NO for production deployment. 
          vaMetadata.quietMode = false; // Set to NO for production deployment. 
          vaMetadata.setEnableChapterTracking(true); 
          // use this API to override the default asset length -1 for live streams 
          vaMetadata.setAssetDuration(SAMPLE_ASSET_DURATION); 
      
          return vaMetadata; 
      }
      ```

   1. Video Analyticsメタデータをグローバルメタデータインスタンスに追加します。

      準備が整ったら、メディアリソースまたはメディアプレイヤー項目にグローバルメタデータインスタンスを設定します。

      ```java
      ((MetadataNode)resourceMetadata).setNode( 
            DefaultMetadataKeys.VIDEO_ANALYTICS_METADATA_KEY.getValue(), vaMetadata);
      ```

   1. ビデオ分析トラッカーを初期化します。

      メディアプレイヤーインスタンスを作成した後、ビデオ分析トラッカーインスタンスを作成し、メディアプレイヤーインスタンスへの参照を指定する必要があります。

      >[!TIP]
      >
      >各コンテンツ再生セッションに対して新しいトラッカーインスタンスを必ず作成し、メディアプレーヤーインスタンスを切り離した後で、以前の参照を削除します。

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider =  
        new VideoAnalyticsProvider(appContext); 
      
      // Attach the TVSDK media player instance 
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. ビデオ分析トラッカーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、数分待ってから、ビデオトラッカーインスタンスを破棄します。 インスタンスをすぐに破棄すると、ビデオ分析トラッカーでビデオ完了のpingを送信する機能が妨げられる可能性があります。

      ```java
      if (_videoAnalyticsProvider) { 
          _videoAnalyticsProvider.detachMediaPlayer(); 
          _videoAnalyticsProvider = null; 
      }
      ```

   1. 手動でライブ/リニアストリームを完了としてマークします。

      1つのライブストリームに複数のエピソードがある場合、Complete APIを使用して、手動でエピソードを完了としてマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >このAPIはオプションで、VODビデオ追跡には必要ありません。

      ```java
      if (_videoAnalyticsProvider) { 
         _videoAnalyticsProvider.trackVideoComplete();    
      }
      ```

