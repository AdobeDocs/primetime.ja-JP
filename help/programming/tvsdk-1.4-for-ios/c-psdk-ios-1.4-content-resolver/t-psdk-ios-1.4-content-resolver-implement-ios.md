---
description: デフォルトのリゾルバーに基づいて、リゾルバーを実装できます。
title: カスタムオポチュニティ/コンテンツリゾルバーの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# カスタムオポチュニティ/コンテンツリゾルバーの実装{#implement-a-custom-opportunity-content-resolver}

デフォルトのリゾルバーに基づいて、リゾルバーを実装できます。

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. を拡張して、カスタム広告リゾルバーを開発する `PTContentResolver` 抽象クラス。

   `PTContentResolver` は、コンテンツリゾルバークラスで実装する必要があるインターフェイスです。 同じ名前の抽象クラスも使用でき、設定を自動的に処理します（デリゲートの取得）。

   >[!TIP]
   >
   >`PTContentResolver` は、 `PTDefaultMediaPlayerClientFactory` クラス。 クライアントは、 `PTContentResolver` 抽象クラス。 デフォルトでは、特に削除されない限り、 `PTDefaultAdContentResolver` が `PTDefaultMediaPlayerClientFactory`.

   ```
   @protocol PTContentResolver <NSObject> 
   @required 
   + (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity;  
   //Detector returns YES/NO if it should handle the following placement opportunity 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                 delegate:(id<PTContentResolverDelegate> delegate); 
   - (void)process:(PTPlacementOpportunity *)opportunity; 
   - (void)timeout:(PTPlacementOpportunity *)opportunity;  
   //The timeout method gets invoked if the TVSDK decides that the  
   //PTContentResolver is taking too much time to respond. 
   @end 
   
   @interface PTContentResolver : NSObject <PTContentResolver> 
   
   @property (readonly) id<PTContentResolverDelegate> delegate; 
   @property (readonly) PTMediaPlayerItem *playerItem; 
   
   - (BOOL)shouldHandleOpportunity:(PTPlacementOpportunity *)opportunity; 
   - (void)configWithPlayerItem:(PTMediaPlayerItem *)item  
                  delegate:(id<PTContentResolverDelegate>) delegate; 
   - (void)process:(NSArray *)opportunities; 
   - (void)cancel:(NSArray *)opportunities; 
   @end
   ```

1. 実装方法 `shouldResolveOpportunity` 戻る `YES` 受信した `PTPlacementOpportunity`.
1. 実装方法 `resolvePlacementOpportunity`：代替コンテンツまたは広告の読み込みを開始します。
1. 広告が読み込まれたら、 `PTTimeline` に、挿入するコンテンツに関する情報を入力します。

       次に、タイムラインに関する便利な情報を示します。
   
   * 複数の `PTAdBreak`プリロール、ミッドロール、ポストロールの各タイプ。

      * A `PTAdBreak` には次の機能があります。

         * A `CMTimeRange` を切断の開始時間と期間に設定します。

           これは、の範囲プロパティとして設定されます。 `PTAdBreak`.

         * `NSArray` / `PTAd`s.

           これは、の ads プロパティとして設定されます。 `PTAdBreak`.

   * A `PTAd` は広告を表し、各広告は `PTAd` には次の機能があります。

      * A `PTAdHLSAsset` を広告のプライマリアセットプロパティとして設定します。
      * 複数の `PTAdAsset` クリック可能な広告またはバナー広告としてのインスタンス。

   例：

   ```
   NSMutableArray *ptBreaks = [[[NSMutableArray alloc] init] autorelease]; 
   
   // Prepare the primary asset of the ad - links to ad m3u8 
   PTAdHLSAsset *ptAdAsset = [[[PTAdHLSAsset alloc] init] autorelease]; 
   ptAdAsset.source = AD_SOURCE_M3U8; 
   ptAdAsset.id = FAKE_NUMBER_ID; 
   ptAdAsset.format = @"video"; 
   
   // Prepare the ad itself. 
   PTAd *ptAd = [[[PTAd alloc] init] autorelease]; 
   ptAd.primaryAsset = ptAdAsset; 
   ptAd.primaryAsset.ad = ptAd; 
   
   // Prepare the break and add the ad created above. 
   PTAdBreak *ptBreak = [[[PTAdBreak alloc] init] autorelease]; 
   ptBreak.relativeRange = CMTimeRangeMake(BREAK_START_TIME, BREAK_DURATION_VALUE); 
   [ptBreak addAd:ptAd]; 
   
   // Add the break to array of breaks. 
   [ptBreaks addObject:adBreak]; 
   
   // Once all breaks have been prepared, they can be set on timeline 
   PTTimeline *_timeline = [[PTTimeline alloc] init]; 
   _timeline.adBreaks = ptBreaks;
   ```

1. 通話 `didFinishResolvingPlacementOpportunity`：を提供します。 `PTTimeline`.
1. を呼び出して、カスタムコンテンツ/広告リゾルバーをデフォルトのメディアプレーヤーファクトリに登録します。 `registerContentResolver`.

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. カスタムオポチュニティリゾルバーを実装した場合は、デフォルトのメディアプレーヤーファクトリに登録します。

   >[!TIP]
   >
   >カスタムコンテンツ/広告リゾルバーを登録するために、カスタムオポチュニティリゾルバーを登録する必要はありません。

   ```
   //Remove default opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearOpportunityResolvers]; 
   
   //Create an instance of your opportunity resolver (id <PTOpportunityResolver>) 
   CustomOpportunityResolver *opportunityResolver = [[CustomOpportunityResolver alloc] init]; 
   
   //Set custom opportunity resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory]  
              registerOpportunityResolver:[opportunityResolver autorelease]];
   ```

プレーヤーがコンテンツを読み込み、VOD または LIVE タイプであると判断されると、次のいずれかが発生します。 >
* コンテンツが VOD の場合、カスタムコンテンツリゾルバーを使用して、ビデオ全体の広告タイムラインを取得します。
* コンテンツが LIVE の場合、コンテンツ内で配置オポチュニティ（キューポイント）が検出されるたびに、カスタムコンテンツリゾルバーが呼び出されます。
