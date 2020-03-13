---
description: 'null'
seo-description: 'null'
seo-title: ビデオ分析の初期化と設定
title: ビデオ分析の初期化と設定
uuid: 98017a20-4997-42f7-9b03-fd9c4b6ccd92
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# ビデオ分析の初期化と設定 {#initialize-and-configure-video-analytics}

ビデオの使用を追跡および分析するようにプレーヤーを設定できます。
ビデオ追跡（ビデオハートビート）をアクティブ化する前に、次の事項を確認します。

* Android向けTVSDK 2.5。
* 設定/初期化情報

   特定のビデオトラッキングアカウント情報については、アドビの担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>重要： このJSON設定ファイル名は、ADBMobileConfig.jsonのま <span class="filepath"> まにする必要がありま </span>す。 この構成ファイルの名前とパスは変更できません。 このファイルへのパスは、 <span class="filepath"> &lt;source root&gt;/assetsである必要があります </span>。 </p> </td> 
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
 </tbody> 
</table>

プレーヤーでビデオトラッキングを設定するには：

1. リソースファイルの読み込み時のオプションが正しい `ADBMobileConfig.json` ことを確認します。

       &quot;
    {
    &quot;version&quot; :&quot;1.1&quot;,
     &quot;analytics&quot;:{
    &quot;rsids&quot; :&quot;adobedevelopment&quot;,
     &quot;server&quot; :&quot;10.131.129.149:3000&quot;,
 &quot;charset&quot;     :&quot;UTF-8&quot;,
 &quot;     ssl&quot; :false,
     &quot;offlineEnabled&quot; :false,
     &quot;lifecycleTimeout&quot; :5,
     &quot;batchLimit&quot; :50,
     &quot;privacyDefault&quot; :&quot;optedin&quot;,
     &quot;poi&quot; :[]
 },     
    &quot;marketingCloud&quot;:{
 &quot;     org&quot;:&quot;ADOBE PROVIDED VALUE&quot;
    },
 &quot;     target&quot; :{
    &quot;clientCode&quot; :&quot;&quot;,
     &quot;timeout&quot; :5
 },     
    &quot;audienceManager&quot; :{
    &quot;server&quot; :&quot;&quot;
 }     
 &quot;     
 &quot;     
    
    JSON形式の設定ファイルは、TVSDKにリソースとしてバンドルされています。 プレイヤーは、読み込み時にのみこれらの値を読み取り、アプリケーションの実行中は値は一定のままです。
   読み込     
    み時間オプションを設定するには：
   
   1. ファイルに適切な `ADBMobileConfig.json` 値（アドビが提供する値）が含まれていることを確認します。
   1. このファイルがフォルダー内にあることを確認 `assets/` します。

      このフォルダーは、アプリケーションのソースツリーのルートに配置する必要があります。

   1. アプリケーションをコンパイルしてビルドします。
   1. バンドルされたアプリケーションをデプロイして実行します。

      これらのAppMeasurement設定について詳しくは、Adobe Analyticsでのビデオの測 [定を参照してください](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/)。

1. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化することができます。 モジュールを再初期化する前に、ビデオ分析のメタデータも正しいコンテンツのメタデータに更新されていることを確認します。 メタデータを再作成するには、次の最初の2つの手順を繰り返し **ます(** aと **b**)。

   1. ビデオ分析メタデータのインスタンスを作成します。

      このインスタンスには、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報が含まれています。 例：

      ```java
      private VideoAnalyticsMetadata getVideoAnalyticsTrackingMetadata() { 
          VideoAnalyticsMetadata vaMetadata = new VideoAnalyticsMetadata(); 
      
          vaMetadata.setTrackingServer("example.com"); 
          vaMetadata.setChannel("test-channel"); 
          vaMetadata.setVideoName("myvideo"); 
          vaMetadata.setVideoId("myvideoid"); 
          vaMetadata.setPlayerName("PSDK Player"); 
          vaMetadata.setUseSSL(false); 
          vaMetadata.debugLogging = true; // Set to NO for production deployment. 
          vaMetadata.setEnableChapterTracking(true); 
          // use this API to override the default asset length -1 for live streams 
          vaMetadata.setAssetDuration(SAMPLE_ASSET_DURATION); 
      
          return vaMetadata; 
      }
      ```

   1. ビデオ分析プロバイダーを初期化します。

      メディアプレイヤーインスタンスを作成した後、Video Analyticsプロバイダーインスタンスを作成し、そのインスタンスにアプリケーションコンテキストを提供する必要があります。

      >[!TIP]
      >
      >各コンテンツ再生セッションに対して必ず新しいプロバイダーインスタンスを作成し、メディアプレーヤーインスタンスを切り離した後で、以前の参照を削除します。

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. インスタンスに対してビデオ分析メタデータを設 `videoAnalyticsProvider` 定します。

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. メディアプレイヤーインスタンスをインスタンスにアタッチ `videoAnalyticsProvider` します。

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. ビデオ分析プロバイダーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオプロバイダーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、数分待ってから、ビデオ分析プロバイダーインスタンスを破棄します。 インスタンスをすぐに破棄すると、ビデオ分析プロバイダーが「ビデオ完了」のpingを送信する機能を妨げる可能性があります。

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. 手動でライブ/リニアストリームを完了としてマークします。

      1つのライブストリームに複数のエピソードがある場合、Complete APIを使用して、手動でエピソードを完了としてマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >このAPIはオプションで、VODビデオ追跡には使用できません。

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```

