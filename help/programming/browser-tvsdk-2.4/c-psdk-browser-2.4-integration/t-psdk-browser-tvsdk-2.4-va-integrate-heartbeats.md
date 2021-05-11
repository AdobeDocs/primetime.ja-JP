---
description: ビデオの使用を追跡および分析するようにプレイヤーを設定できます。
title: ビデオ分析の初期化と設定
exl-id: e0bf461b-a431-4fba-bd3d-c38be307a92f
translation-type: tm+mt
source-git-commit: d884836a2a585bd3540b085de1098cf6ae3de46b
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# ビデオ分析の初期化と設定{#initialize-and-configure-video-analytics}

ビデオの使用を追跡および分析するようにプレイヤーを設定できます。

ビデオトラッキング（ビデオハートビート）をアクティブ化する前に、以下があることを確認します。

* 設定/ブラウザTVSDKの初期化情報 — 特定のビデオトラッキングアカウント情報については、Adobeの担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
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
  <tr>
   <td colname="col1"> 訪問者トラッキングサーバーエンドポイント </td>
   <td colname="col2"> 現在のビデオビューアの一意の識別子を提供するバックエンドのエンドポイントのURL。 </td>
  </tr>
  <tr>
   <td colname="col1"> 投稿者 </td>
   <td colname="col2"> これはPublisher IDで、Adobeの担当者からお客様に提供されます。 <p>ヒント： このIDは、単なるブランド名やテレビ名を持つ文字列ではありません。 </p> </td>
  </tr>
 </tbody>
</table>

プレーヤーでビデオトラッキングを設定するには：

1. VisitorAPIライブラリをインスタンス化し、設定します。

       次の情報に注意してください。
   
   * インスタンス化には、Adobeが提供するMarketing Cloud組織ID入力パラメーターが必要です。

      これは文字列値です。
   * VisitorAPIライブラリの唯一の設定オプションは、現在のユーザーの一意の識別子を提供するバックエンドエンドポイントのURLです。
   * 訪問者トラッキングサーバーのURLは、AnalyticsトラッキングサーバーのURLと同じです。

      訪問者IDサービスの実装について詳しくは、[訪問者IDサービスの実装](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html)を参照してください。

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. AppMeasurementコンポーネントをインスタンス化し、設定します。

   AppMeasurementインスタンスには、多くの設定オプションがあります。 詳しくは、[Adobe Analytics開発者](https://microsite.omniture.com/t2/help/en_US/reference/#Developer)のドキュメントを参照してください。 次のサンプルコード(`account`、`visitorNamespace`、`trackingServer`)のオプションは必須で、値はAdobeで提供されます。

   >[!IMPORTANT]
   >
   >依存関係チェーンが正しく設定されていることを確認する必要があります。 AppMeasurementインスタンスの集計(訪問者APIコンポーネントに依存)。

   ```js
   var appMeasurement = new AppMeasurement();
   appMeasurement.visitor = visitor;
   appMeasurement.trackingServer = 'URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER';
   appMeasurement.account = 'ACCOUNT_NAME'; // Also known as RSID
   appMeasurement.pageName = 'Sample Page Name';
   appMeasurement.charSet = "UTF-8";
   appMeasurement.visitorID = "test-vid";
   ```

   >[!IMPORTANT]
   >
   >アプリケーションで、ビデオ分析のフローを開始する前に`appMeasurementObject.visitor`が設定されていることを確認してください。設定されていないと、トラッキング結果が得られない場合があります。 これらの結果は、ログ内のメッセージで示されます。 空のトラック呼び出し(`appMeasurementObject.track`)を追加し、設定されるまで`visitor`プロパティをポーリングして、ビデオ分析を開始できます。

3. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化できます。 モジュールを再初期化する前に、ビデオ分析メタデータも正しいコンテンツメタデータに更新されていることを確認します。 メタデータを再作成するには、手順1と2を繰り返します。

   1. ビデオ分析メタデータのインスタンスを作成します。
このインスタンスは、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報を含みます。 例：

      ```js
      function getVideoAnalyticsMetadata() {
          var vaObj = new AdobePSDK.VA.VideoAnalyticsMetadata();
          vaObj.appMeasurement = appMeasurement;
          vaObj.trackingServer = 'hbTrackingServer';
          vaObj.publisher = 'hbPublisher';
          vaObj.channel = 'sample-channel';
          vaObj.playerName = 'TVSDK-HTML';
          vaObj.appVersion = '1.0.0';
          vaObj.videoName = 'hbFriendlyName'; // this will overwrite the ContextData variable a.media.friendlyName
          vaObj.assetDuration = durationInSeconds;
          // use this to override the default asset length of -1 for live streams
          vaObj.debugLogging = false;
          return vaObj;
      }
      ```

   2. メディアプレイヤーインスタンスを作成したら、ビデオ分析トラッカーインスタンスを作成し、メディアプレイヤーインスタンスの参照を指定します。
次の点に注意してください。

      * コンテンツ再生セッションごとに新しいトラッカーインスタンスを必ず作成し、（メディアプレイヤーインスタンスを切り離した後で）以前の参照を削除してください。
      * サブ手順1で作成したメタデータは、Video Analytics Trackerのコンストラクターで提供する必要があります。

         ```js
         var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
         videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
         videoAnalyticsProvider.attachMediaPlayer(player);
         ```
   3. ビデオ分析トラッカーを破棄します。
新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、ビデオトラッカーインスタンスを破棄するまで数分待ちます。 インスタンスをすぐに破棄すると、ビデオ分析トラッカーがビデオ完了pingを送信する機能を妨げる可能性があります。

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```

   4. 手動でライブ/リニアストリームを完了としてマークします。
1つのライブストリームに様々なエピソードがある場合、完了APIを使用して、手動でエピソードを完了とマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。
      >[!TIP]
      >
      >このAPIはオプションで、VODビデオトラッキングには必要ありません。

      ```js
      if (videoAnalyticsProvider)
      {
         videoAnalyticsProvider.trackVideoComplete();
      videoAnalyticsProvider.detachMediaPlayer();
      videoAnalyticsProvider = null;
      // Create a new instance of VideoAnalyticsProvider to continue tracking.
      }
      ```
