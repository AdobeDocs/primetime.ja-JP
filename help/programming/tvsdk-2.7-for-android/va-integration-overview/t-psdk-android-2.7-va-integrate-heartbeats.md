---
title: ビデオ分析の初期化と設定
description: ビデオ分析の初期化と設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---


# ビデオ分析の初期化と設定{#initialize-and-configure-video-analytics}

ビデオの使用を追跡および分析するようにプレイヤーを設定できます。
ビデオトラッキング（ビデオハートビート）をアクティブ化する前に、以下があることを確認します。

* Android向けTVSDK 2.5。
* 構成/初期化情報

   特定のビデオトラッキングアカウント情報については、Adobeの担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>重要： このJSON設定ファイル名は<span class="filepath"> ADBMobileConfig.json </span>のままにしておく必要があります。 この構成ファイルの名前とパスは変更できません。 このファイルへのパスは、<span class="filepath"> &lt;source root&gt;/assets </span>でなければなりません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AppMeasurementトラッキングサーバーエンドポイント </td> 
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


   1. `ADBMobileConfig.json`ファイルに(Adobeが提供する)適切な値が含まれていることを確認します。
   1. このファイルが`assets/`フォルダー内にあることを確認します。

      このフォルダーは、アプリケーションソースツリーのルートに存在する必要があります。

   1. アプリケーションをコンパイルしてビルドします。
   1. バンドルされたアプリケーションをデプロイして実行します。

      これらのAppMeasurement設定について詳しくは、[Adobe Analyticsでのビデオの測定](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/)を参照してください。

1. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化できます。 モジュールを再初期化する前に、ビデオ分析メタデータも正しいコンテンツメタデータに更新されていることを確認します。 メタデータを再作成するには、次の最初の2つの手順を繰り返します（サブ手順&#x200B;**a**&#x200B;と&#x200B;**b**）。

   1. ビデオ分析メタデータのインスタンスを作成します。

      このインスタンスは、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報を含みます。 例：

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

      メディアプレイヤーインスタンスを作成したら、ビデオ分析プロバイダーインスタンスを作成し、そのインスタンスにアプリケーションコンテキストを提供する必要があります。

      >[!TIP]
      >
      >コンテンツ再生セッションごとに必ず新しいプロバイダーインスタンスを作成し、メディアプレイヤーインスタンスを切り離した後で、以前の参照を削除してください。

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. `videoAnalyticsProvider`インスタンスにVideo Analyticsメタデータを設定します。

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. メディアプレイヤーインスタンスを`videoAnalyticsProvider`インスタンスに接続します。

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. ビデオ分析プロバイダーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオプロバイダーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、ビデオ分析プロバイダーインスタンスを破棄するまで数分待ちます。 インスタンスを直ちに破棄すると、Video Analyticsプロバイダーが「ビデオ完了」pingを送信する機能を妨げる可能性があります。

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. 手動でライブ/リニアストリームを完了としてマークします。

      1つのライブストリームに様々なエピソードがある場合、完了APIを使用して、手動でエピソードを完了とマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >このAPIはオプションで、VODビデオトラッキングでは機能しません。

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```

