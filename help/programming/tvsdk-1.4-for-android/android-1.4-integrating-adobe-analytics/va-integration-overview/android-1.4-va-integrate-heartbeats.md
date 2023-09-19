---
description: プレーヤーを設定して、ビデオの使用状況を追跡し分析できます。
title: ビデオ分析を初期化して設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# ビデオ分析を初期化して設定{#initialize-and-configure-video-analytics}

プレーヤーを設定して、ビデオの使用状況を追跡し分析できます。

ビデオトラッキング（ビデオハートビート）をアクティブ化する前に、以下があることを確認します。

* Android 向け TVSDK
* 設定/初期化情報 — 特定のビデオトラッキングアカウント情報については、Adobe担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>重要：この JSON 設定ファイル名は残しておく必要があります <span class="codeph"> ADBMobileConfig.json </span>. この設定ファイルの名前とパスは変更できません。 このファイルへのパスは次のようにする必要があります。 <span class="codeph"> &lt;source root=""&gt;/assets </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AppMeasurementトラッキングサーバーエンドポイント </td> 
   <td colname="col2"> Adobe Analytics( 旧称、SiteCatalyst) のバックエンド収集エンドポイントの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ビデオ分析トラッキングサーバーエンドポイント </td> 
   <td colname="col2"> ビデオ分析のバックエンド収集エンドポイントの URL。 すべてのビデオハートビートトラッキングコールが送信される場所です。 <p>ヒント：訪問者トラッキングサーバーの URL は、Analytics トラッキングサーバーの URL と同じです。 訪問者 ID サービスの導入について詳しくは、 <a href="https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en" format="html" scope="external"> ID サービスの実装 </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アカウント名 </td> 
   <td colname="col2"> レポートスイート ID(RSID) とも呼ばれます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Marketing Cloud組織 ID </td> 
   <td colname="col2"> 訪問者コンポーネントのインスタンス化に必要な string 値。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 投稿者 </td> 
   <td colname="col2"> これは Publisher ID で、ユーザーのAdobe担当者から提供されます。 <p>ヒント：この ID は、単なるブランド名またはテレビ名を含む文字列ではありません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

プレーヤーでビデオトラッキングを設定するには：

1. 読み込み時間オプションを `ADBMobileConfig.json` リソースファイルが正しい。

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

   この JSON 形式の設定ファイルは、TVSDK にリソースとしてバンドルされています。 プレーヤーは、読み込み時にのみこれらの値を読み取り、アプリケーションの実行中は値が一定に保たれます。

   読み込み時間オプションを設定するには：

   1. を確認します。 `ADBMobileConfig.json` file には、Adobeで提供される適切な値が含まれます。
   1. このファイルが `assets` フォルダー。

      このフォルダーは、アプリケーションソースツリーのルートに配置する必要があります。
   1. アプリケーションをコンパイルしてビルドします。
   1. バンドルされたアプリケーションをデプロイして実行します。

      これらの設定について詳しくは、「AppMeasurement設定」を参照してください。 [Adobe Analyticsでのビデオの測定](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=en).
1. ビデオハートビートトラッキングメタデータを初期化して設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化できます。 モジュールを再初期化する前に、ビデオ分析メタデータも正しいコンテンツメタデータに更新されていることを確認します。 メタデータを再作成するには、手順 1 と 2 を繰り返します。

   1. Video Analytics メタデータのインスタンスを作成します。

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

   1. グローバルメタデータインスタンスにビデオ分析メタデータを追加します。

      準備が整ったら、メディアリソースまたはメディアプレーヤーアイテムにグローバルメタデータインスタンスを設定します。

      ```java
      ((MetadataNode)resourceMetadata).setNode( 
            DefaultMetadataKeys.VIDEO_ANALYTICS_METADATA_KEY.getValue(), vaMetadata);
      ```

   1. ビデオ分析トラッカーを初期化します。

      Media Player インスタンスを作成した後、Video Analytics トラッカーインスタンスを作成し、Media Player インスタンスへの参照を指定する必要があります。

      >[!TIP]
      >
      >各コンテンツ再生セッションに対して新しいトラッカーインスタンスを必ず作成し、メディアプレーヤーインスタンスを分離した後で、以前の参照を削除します。

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider =  
        new VideoAnalyticsProvider(appContext); 
      
      // Attach the TVSDK media player instance 
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. ビデオ分析トラッカーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、ビデオトラッカーインスタンスを破棄するまで数分待ちます。 インスタンスを直ちに破棄すると、ビデオ分析トラッカーがビデオ完了 ping を送信する機能を妨げる場合があります。

      ```java
      if (_videoAnalyticsProvider) { 
          _videoAnalyticsProvider.detachMediaPlayer(); 
          _videoAnalyticsProvider = null; 
      }
      ```

   1. ライブ/リニアストリームを手動で完了とマークします。

      1 つのライブストリームに様々なエピソードがある場合、完全な API を使用して、エピソードを手動で完了とマークできます。 これにより、現在のビデオのエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >この API はオプションで、VOD ビデオトラッキングには不要です。

      ```java
      if (_videoAnalyticsProvider) { 
         _videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
