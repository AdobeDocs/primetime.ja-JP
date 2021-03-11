---
description: デフォルトのリゾルバーに基づいてリゾルバーを実装できます。
title: カスタムオポチュニティ/コンテンツリゾルバーの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# カスタムオポチュニティ/コンテンツリゾルバーの実装{#implement-a-custom-opportunity-content-resolver}

デフォルトのリゾルバーに基づいてリゾルバーを実装できます。

<!--<a id="fig_CC41E2A66BDB4115821F33737B46A09B"></a>-->

![](assets/ios_psdk_content_resolver.png)

1. `PTContentResolver`抽象クラスを拡張して、カスタム広告リゾルバーを開発します。

   `PTContentResolver` は、コンテンツリゾルバークラスで実装する必要があるインターフェイスです。同じ名前の抽象クラスも使用でき、設定を自動的に処理（委任の取得）します。

   >[!TIP]
   >
   >`PTContentResolver` は、 `PTDefaultMediaPlayerClientFactory` クラスを通じて公開されます。クライアントは、`PTContentResolver`抽象クラスを拡張することで、新しいコンテンツリゾルバーを登録できます。 デフォルトでは、特別に削除しない限り、`PTDefaultAdContentResolver`は`PTDefaultMediaPlayerClientFactory`に登録されます。

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

1. `shouldResolveOpportunity`を実装し、受信した`PTPlacementOpportunity`を処理する必要がある場合は`YES`を返します。
1. 代替コンテンツまたは広告を読み込む開始を`resolvePlacementOpportunity`に実装します。
1. 広告が読み込まれたら、挿入するコンテンツに関する情報を`PTTimeline`に準備します。

       以下に、タイムラインに関する有益な情報を示します。
   
   * プリロール、ミッドロール、ポストロールのタイプは複数`PTAdBreak`にすることができます。

      * `PTAdBreak`は次のものです。

         * 開始時間と時間の長さの`CMTimeRange`。

            これは`PTAdBreak`の範囲プロパティとして設定されます。

         * `NSArray` の値 `PTAd`。

            これは`PTAdBreak`の広告プロパティとして設定されます。
   * `PTAd`は広告を表し、各`PTAd`は次のものを持ちます。

      * 広告の主なアセットプロパティとして設定される`PTAdHLSAsset`。
      * クリック可能な広告またはバナー広告として複数の`PTAdAsset`インスタンスが存在する可能性があります。

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

1. `didFinishResolvingPlacementOpportunity`を呼び出します。これにより、`PTTimeline`が提供されます。
1. `registerContentResolver`を呼び出して、カスタムコンテンツ/広告リゾルバーをデフォルトのメディアプレイヤーファクトリに登録します。

   ```
   //Remove default content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] clearContentResolvers]; 
   
   //Create an instance of your content/ad resolver (id <PTContentResolver>) 
   CustomContentResolver *contentResolver = [[CustomContentResolver alloc] init]; 
   
   //Set custom content/ad resolver 
   [[PTDefaultMediaPlayerFactory defaultFactory] registerContentResolver:[contentResolver autorelease]];
   ```

1. カスタムオポチュニティリゾルバーを実装した場合、それをデフォルトのメディアプレイヤーファクトリに登録します。

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

プレイヤーがコンテンツを読み込み、VODまたはLIVEのタイプであると判断されると、次のいずれかが発生します。>
* コンテンツがVODの場合、カスタムコンテンツリゾルバーを使用して、ビデオ全体の広告タイムラインを取得します。
* コンテンツがLIVEの場合、配置オポチュニティ（キューポイント）がコンテンツ内で検出されるたびに、カスタムコンテンツリゾルバーが呼び出されます。
