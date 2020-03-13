---
description: デフォルトのリゾルバーに基づいてリゾルバーを実装できます。
seo-description: デフォルトのリゾルバーに基づいてリゾルバーを実装できます。
seo-title: カスタムオポチュニティ/コンテンツリゾルバーの実装
title: カスタムオポチュニティ/コンテンツリゾルバーの実装
uuid: bfc14318-ca4b-46cc-8128-e3743af06d9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタムオポチュニティ/コンテンツリゾルバーの実装{#implement-a-custom-opportunity-content-resolver}

デフォルトのリゾルバーに基づいてリゾルバーを実装できます。

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. 抽象クラスを拡張して、カスタム広告リゾルバーを `PTContentResolver` 開発します。

   `PTContentResolver` は、コンテンツリゾルバークラスによって実装する必要があるインターフェイスです。 同じ名前の抽象クラスも使用でき、設定を自動的に処理（委譲を取得）します。

   >[!TIP]
   >
   >`PTContentResolver` は、クラスを通じて公開さ `PTDefaultMediaPlayerClientFactory` れます。 クライアントは、抽象クラスを拡張することで、新しいコンテンツリゾルバーを `PTContentResolver` 登録できます。 デフォルトでは、特に削除しない限り、はに `PTDefaultAdContentResolver` 登録されています `PTDefaultMediaPlayerClientFactory`。

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

1. 受信した `shouldResolveOpportunity` データを処 `YES` 理する必要がある場合は、実装して返しま `PTPlacementOpportunity`す。
1. 代替コ `resolvePlacementOpportunity`ンテンツまたは広告の読み込みを開始する実装。
1. 広告が読み込まれたら、挿入するコンテ `PTTimeline` ンツに関する情報を含む広告を準備します。

       以下に、タイムラインに関する有益な情報を示します。
   
   * プリロール、ミッ `PTAdBreak`ドロール、ポストロールのタイプは複数あります。

      * には次 `PTAdBreak` のものがあります。

         * 時間 `CMTimeRange` の開始時間と時間の長さを示す。

            これは、の範囲プロパティとして設定されま `PTAdBreak`す。

         * `NSArray` の `PTAd`数

            これは、のadsプロパティとして設定されま `PTAdBreak`す。
   * Aは広 `PTAd` 告を表し、各広告には次の `PTAd` ものがあります。

      * 広告の `PTAdHLSAsset` プライマリアセットプロパティとしてのセット。
      * クリック可能な広告ま `PTAdAsset` たはバナー広告として複数のインスタンスが含まれる場合があります。
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

1. を呼び `didFinishResolvingPlacementOpportunity`出し、を提供しま `PTTimeline`す。
1. を呼び出して、カスタムコンテンツ/広告リゾルバーをデフォルトのメディアプレイヤーファクトリに登録しま `registerContentResolver`す。

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. カスタムオポチュニティリゾルバーを実装している場合は、デフォルトのメディアプレイヤーファクトリに登録します。

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

プレーヤーがコンテンツを読み込み、VODまたはLIVEのタイプであると判断されると、次のいずれかが発生します。>
* コンテンツがVODの場合、カスタムコンテンツリゾルバーを使用して、ビデオ全体の広告タイムラインが取得されます。
* コンテンツがLIVEの場合、配置オポチュニティ（キューポイント）がコンテンツ内で検出されるたびに、カスタムコンテンツリゾルバーが呼び出されます。
