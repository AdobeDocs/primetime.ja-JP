---
description: プレーヤーを設定して、ビデオの使用状況を追跡および分析できます。
title: ビデオ分析の初期化と設定
exl-id: 58d560d1-f668-4e1d-a817-b2e02008fdbe
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# ビデオ分析の初期化と設定{#initialize-and-configure-video-analytics}

プレーヤーを設定して、ビデオの使用状況を追跡および分析できます。

ビデオトラッキング（ビデオハートビート）をアクティブ化する前に、以下があることを確認します。

* Desktop HLS 向け TVSDK
* 設定/初期化情報 — 特定のビデオトラッキングアカウント情報については、Adobe担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> AppMeasurement トラッキングサーバーエンドポイント </td> 
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
   <td colname="col1"> 訪問者トラッキングサーバーエンドポイント </td> 
   <td colname="col2"> 現在のビデオビューアの一意の識別子を提供するバックエンドのエンドポイントの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 発行者 </td> 
   <td colname="col2"> これは Publisher ID で、Adobe担当者から顧客に提供されます。 <p>ヒント： この ID は、単なるブランド名/テレビ名の文字列ではありません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

プレーヤーでビデオトラッキングを設定するには：

1. VisitorAPI ライブラリをインスタンス化し、設定します。

       次の情報に留意してください。
   
   * インスタンス化には、Marketing Cloudが提供する組織 ID 入力パラメーターが必要です。Adobe

      これは文字列値です。
   * VisitorAPI ライブラリの唯一の設定オプションは、現在のユーザーの一意の識別子を提供するバックエンドエンドエンドポイントの URL です。
   * 訪問者トラッキングサーバーの URL は、Analytics トラッキングサーバーの URL と同じです。

      訪問者 ID サービスの実装について詳しくは、訪問者 ID サービスの実装を参照してください。

   ```
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID"); 
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”; 
   ```

1. AppMeasurement コンポーネントをインスタンス化し、設定します。

   AppMeasurement インスタンスには、多くの設定オプションがあります。 詳しくは、[Adobe Analytics Developer](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) のドキュメントを参照してください。 次のサンプルコード ( `account`、 `visitorNamespace`、 `trackingServer` ) のオプションが必要です。値はAdobeで提供されます。

   >[!IMPORTANT]
   >
   >依存関係チェーンが正しく設定されていることを確認する必要があります。 AppMeasurement インスタンスは、訪問者 API コンポーネントを集計（依存）します。

   ```
   // Instantiate and configure AppMeasurement 
   
   // Instantiate AppMeasurement instance only once! 
   if (_appMeasurementObject == null) {  
       _appMeasurementObject = new AppMeasurement(); 
   } 
   
   with (_appMeasurementObject) { 
       account = "ACCOUNT_NAME"; // Also known as RSID 
       trackingServer = "URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER"; 
   
       // Use the same value here as for the Visitor API component 
       visitorNamespace = "MARKETING_CLOUD_ORG_ID"; 
   
       // Attach the Visitor API to the AppMeasurement instance. 
       visitor = _visitor;  
       pageName = "pageName"; 
       charSet = "UTF-8"; 
       currencyCode = "USD"; 
   } 
   ```

   >[!IMPORTANT]
   >
   >アプリケーションで、ビデオ分析フローを開始する前に `appMeasurementObject.visitor` が設定されていることを確認してください。設定されていない場合は、トラッキング結果が表示されない場合があります。 これらの結果は、ログのメッセージで示されます。 空のトラック呼び出し (`appMeasurementObject.track`) を追加し、設定されるまで `visitor` プロパティをポーリングして、ビデオ分析を開始できます。

1. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化できます。 モジュールを再初期化する前に、ビデオ分析メタデータも正しいコンテンツメタデータに更新されていることを確認します。 メタデータを再作成するには、手順 1 と 2 を繰り返します。

   1. ビデオ分析メタデータのインスタンスを作成します。

      このインスタンスには、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報が含まれています。 例：

      ```
      private function getVideoAnalyticsTrackingMetadata():VideoAnalyticsMetadata {     
          // Initialize visitor id service and appMeasurement      
          [...] // as shown in the previous steps     
      
          var vaMetadata:VideoAnalyticsMetadata = new VideoAnalyticsMetadata(); 
      
          with (vaMetadata) { 
              trackingServer = "hbTrackingServer"; 
              publisher = "hbPublisher"; 
              channel = "hbChannel";  
              playerName = "hbPlayerName"; 
      
              // this overwrites the ContextData variable a.media.friendlyName 
              videoName = "hbFriendlyName";  
      
              // this will overwrite the ContextData variable a.media.name 
              videoId = "hbName"; 
      
              enableChapterTracking = true; 
      
              // Set these to false for production deployment 
              debugLogging = true;  
              quietMode = false; 
      
          } 
      } 
      ```

   1. ビデオ分析メタデータをグローバルメタデータインスタンスに追加します。

      準備が整ったら、メディアリソースまたはメディアプレーヤーアイテムにグローバルメタデータインスタンスを設定します。

      ```
      var resourceMetadata:Metadata = _player.currentItem.resource.metadata; 
      resourceMetadata.setMetadata(DefaultMetadataKeys.VIDEO_ANALYTICS_METADATA_KEY,  
                                   getVideoAnalyticsTrackingMetadata());
      ```

   1. ビデオ分析トラッカーを初期化します。

      メディアプレーヤーインスタンスを作成した後、ビデオ分析トラッカーインスタンスを作成し、メディアプレーヤーインスタンスへの参照を指定する必要があります。

      >[!TIP]
      >
      >コンテンツ再生セッションごとに新しいトラッカーインスタンスを作成し、メディアプレーヤーインスタンスを分離した後で、以前の参照を必ず削除してください。

      ```
      _videoAnalyticsProvider = new VideoAnalyticsProvider(_appMeasurementObject); 
      _videoAnalyticsProvider.attachMediaPlayer(_player);
      ```

   1. ビデオ分析トラッカーを破棄します。

      新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、ビデオトラッカーインスタンスを破棄するまで数分待ちます。 インスタンスを直ちに破棄すると、ビデオ分析トラッカーがビデオ完了 ping を送信する機能を妨げる可能性があります。

      ```
      if (videoAnalyticsTracker) { 
          videoAnalyticsTracker.detachMediaPlayer(); 
          videoAnalyticsTracker = null; 
      }
      ```

   1. ライブ/リニアストリームを手動で完了とマークします。

      1 つのライブストリームに様々なエピソードがある場合、完全な API を使用して、エピソードを手動で完了とマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。

      >[!TIP]
      >
      >この API はオプションで、VOD ビデオトラッキングには不要です。
