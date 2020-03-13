---
description: ビデオの使用を追跡および分析するようにプレーヤーを設定できます。
seo-description: ビデオの使用を追跡および分析するようにプレーヤーを設定できます。
seo-title: ビデオ分析の初期化と設定
title: ビデオ分析の初期化と設定
uuid: 4a582b35-ae92-4557-806d-e174fc878cc5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ビデオ分析の初期化と設定 {#initialize-and-configure-video-analytics}

ビデオの使用を追跡および分析するようにプレーヤーを設定できます。

ビデオ追跡（ビデオハートビート）をアクティブ化する前に、次の事項を確認します。

* 設定/ブラウザーTVSDKの初期化情報 — 特定のビデオトラッキングアカウント情報については、アドビの担当者にお問い合わせください。

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
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
   <td colname="col1"> 訪問者トラッキングサーバーエンドポイント </td>
   <td colname="col2"> 現在のビデオビューアの一意の識別子を提供するバックエンドエンドポイントのURL。 </td>
  </tr>
  <tr>
   <td colname="col1"> 投稿者 </td>
   <td colname="col2"> これはPublisher IDで、アドビの担当者が顧客に提供します。 <p>ヒント： このIDは、単なるブランド名やテレビ名を持つ文字列ではありません。 </p> </td>
  </tr>
 </tbody>
</table>

プレーヤーでビデオトラッキングを設定するには：

1. VisitorAPIライブラリをインスタンス化し、設定します。

       次の情報に注意してください。
   
   * インスタンス化には、アドビが提供するMarketing Cloud組織ID入力パラメーターが必要です。

      これは文字列値です。
   * VisitorAPIライブラリの唯一の設定オプションは、現在のユーザーの一意の識別子を提供するバックエンドエンドポイントのURLです。
   * 訪問者トラッキングサーバーのURLは、AnalyticsトラッキングサーバーのURLと同じです。

      訪問者IDサービスの実装について詳しくは、訪問者IDサービ [スの実装を参照してください](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html)。

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. AppMeasurementコンポーネントをインスタンス化し、設定します。

   AppMeasurementインスタンスには、多くの設定オプションがあります。 詳しくは、 [Adobe Analytics Developerドキュメントを参照して](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) ください。 次のサンプルコード(、および `account`)のオ `visitorNamespace`プショ `trackingServer`ンは必須で、値はアドビが提供します。

   >[!IMPORTANT]
   >
   >依存関係チェーンが正しく設定されていることを確認する必要があります。 AppMeasurementインスタンスは、訪問者APIコンポーネントを集約（依存）します。

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
   >ビデオ分析フローを開始する前に、が `appMeasurementObject.visitor` 設定されていることをアプリケーションで確認してください。設定されていない場合は、追跡結果が表示されない可能性があります。 これらの結果は、ログ内のメッセージで示されます。 空のtrack呼び出し( `appMeasurementObject.track`)を追加し、プロパティが設定さ `visitor` れるまでプロパティをポーリングし、ビデオ分析を開始できます。

3. ビデオハートビートトラッキングメタデータを初期化し、設定します。

   >[!IMPORTANT]
   >
   >ビデオ分析モジュールのミッドストリームを停止し、必要に応じて再初期化することができます。 モジュールを再初期化する前に、ビデオ分析のメタデータも正しいコンテンツのメタデータに更新されていることを確認します。 メタデータを再作成するには、手順1と2を繰り返します。

   1. ビデオ分析メタデータのインスタンスを作成します。
このインスタンスには、ビデオハートビートトラッキングを有効にするために必要なすべての設定情報が含まれています。 例：

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

   2. メディアプレイヤーインスタンスを作成した後、ビデオ分析トラッカーインスタンスを作成し、メディアプレイヤーインスタンスへの参照を指定します。
次の点に注意してください。

      * 各コンテンツ再生セッションに対して新しいトラッカーインスタンスを必ず作成し、（メディアプレーヤーインスタンスを切り離した後で）以前の参照を削除します。
      * サブ手順1で作成されたメタデータは、ビデオ分析トラッカーのコンストラクターで指定する必要があります。

         ```js
         var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
         videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
         videoAnalyticsProvider.attachMediaPlayer(player);
         ```
   3. ビデオ分析トラッカーを破棄します。
新しいコンテンツ再生セッションを開始する前に、ビデオトラッカーの以前のインスタンスを破棄します。 コンテンツ完了イベント（または通知）を受け取ったら、数分待ってから、ビデオトラッカーインスタンスを破棄します。 インスタンスをすぐに破棄すると、ビデオ分析トラッカーでビデオ完了のpingを送信する機能が妨げられる可能性があります。

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```
   4. 手動でライブ/リニアストリームを完了としてマークします。
1つのライブストリームに複数のエピソードがある場合、Complete APIを使用して、手動でエピソードを完了としてマークできます。 これにより、現在のビデオエピソードのビデオトラッキングセッションが終了し、次のエピソードの新しいトラッキングセッションを開始できます。
      >[!TIP]
      >
      >このAPIはオプションで、VODビデオ追跡には必要ありません。

      ```js
      if (videoAnalyticsProvider)
      {
         videoAnalyticsProvider.trackVideoComplete();
      videoAnalyticsProvider.detachMediaPlayer();
      videoAnalyticsProvider = null;
      // Create a new instance of VideoAnalyticsProvider to continue tracking.
      } 
      ```
