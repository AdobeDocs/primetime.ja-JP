---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
seo-description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
seo-title: カスタムコンテンツリゾルバーの実装
title: カスタムコンテンツリゾルバーの実装
uuid: 5f63cc1e-3f4b-460c-9151-2b9d364800e2
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# カスタムコンテンツリゾルバーの実装 {#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

TVSDKは、新しいオポチュニティを生成する際に、登録されたコンテンツリゾルバーを繰り返し処理し、そのオポチュニティを解決できるコンテンツリゾルバーを探します。 最初に返されたオポチュニテ `true` ィが選択され、そのオポチュニティが解決されます。 コンテンツリゾルバーに対応していない場合、そのオポチュニティはスキップされます。 コンテンツ解決プロセスは通常非同期なので、コンテンツリゾルバーは、プロセスが完了したことをTVSDKに通知します。

1. インターフェイスを拡張し `ContentFactory`て上書きすることで、独自のカ `ContentFactory` スタムを実装しま `retrieveResolvers`す。

   例：

   ```java
   class MyContentFactory extends ContentFactory { 
       @Override 
       public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { 
           List<ContentResolver> resolvers = new ArrayList<ContentResolver>(); 
           MediaPlayerItemConfig itemConfig = item.getConfig(); 
           if(itemConfig) { 
               CustomRangeMetadata customRanges = itemConfig.getCustomRangeMetadata(); 
               if (customRanges) { 
                   List<ReplaceTimeRange> timeRanges = customRanges.getTimeRangeList(); 
   
                   if (timeRanges && timeRanges.size() > 0) 
                   { 
                   // CustomRangeResolver is only activated by the presence of CustomRanges in configuration 
                   resolvers.add(new CustomRangeResolver()); 
                   } 
               } 
               AdvertisingMetadata metadata = itemConfig.getAdvertisingMetadata(); 
               if (metadata) { 
                   if (metadata instanceOf AuditudeSettings)  
                       resolvers.add(new AuditudeResolver(getContext());    
                   } 
               } 
           // add your custom resolver if any 
           resolvers.add(MyOpportunityGenerator(item)); 
           return resolvers; 
       } 
       ... 
   } 
   ```

1. をに登 `ContentFactory` 録します `MediaPlayer`。

   例：

   ```java
   //Register the custom content factory with the media player 
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new MyContentFactory()); 
   
   //Pass this config while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config); 
   
   // OR use MediaPlayerItemLoader to pre-load a resource 
   id = 23; 
   itemLoader.load(resource, id, config);
   ```

1. 次の手順でTVSDK `AdvertisingMetadata` にオブジェクトを渡します。
   1. オブジェクトを作 `AdvertisingMetadata` 成します。
   1. オブジェクトを `AdvertisingMetadata` に保存しま `MediaPlayerItemConfig`す。

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. クラスを拡張するカスタム広告リゾルバークラスを作成 `ContentResolver` します。
   1. カスタム広告リゾルバーで、override `doConfigure`、 `doCanResolve`、、 `doResolve`、 `doCleanup`:

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      渡された項 `advertisingMetadata` 目から、次の情報を取得しま `doConfigure`す。

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. 配置オポチュニティごとに、を作成しま `List<TimelineOperation>`す。

      このサンプル `TimelineOperation` は、次の構造を提供しま `AdBreakPlacement`す。

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. 広告が解決されたら、次のいずれかの関数を呼び出します。

      * 広告の解決に成功した場合は、を呼 `process(List<TimelineOperation> proposals)` び出し `notifyCompleted(Opportunity opportunity)` 、 `ContentResolverClient`

         ```java
         _client.process(timelineOperations); 
         _client.notifyCompleted(opportunity); 
         ```

      * 広告の解決に失敗した場合は、 `notifyResolveError``ContentResolverClient`

         ```java
         _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
         ```

         例：

         ```java
         _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
         ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

このサンプルのカスタム広告リゾルバーは、オポチュニティを解決し、単純な広告を提供します。

```java
public class CustomContentResolver extends ContentResolver { 
    protected void doConfigure(MediaPlayerItem item){} 
 
    protected boolean doCanResolve(Opportunity opportunity) {  
        return true;  
    } 
 
    protected void doResolve(Opportunity opportunity) { 
        _client.process(createAdBreakPlacementsFor(opportunity.getPlacement())); 
        _client.notifyCompleted(opportunity); 
    } 
 
    private List<TimelineOperation> createAdBreakPlacementsFor(Placement placementInformation) { 
        List<Ad> ads = new ArrayList<Ad>(); 
        AdAsset adAsset = new AdAsset("101", 15000, new MediaResource( 
          "https: . . ..m3u8", MediaResource.Type.HLS, null), null, null); 
 
        Ad ad = Ad.linearFromAsset("101", adAsset, null, null, false); 
        ads.add(ad); 
        AdBreak adBreak = new AdBreak(ads, null, AdInsertionType.CLIENT_INSERTED); 
 
        List<TimelineOperation> result = new ArrayList<TimelineOperation>(); 
 
        result.add(new AdBreakPlacement(placementInformation, adBreak)); 
        return result; 
    } 
 
    protected void doCleanup() {} 
} 
```

