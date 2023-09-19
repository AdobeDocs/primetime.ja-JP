---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
title: カスタムコンテンツリゾルバーの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# カスタムコンテンツリゾルバーの実装 {#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

TVSDK は、新しいオポチュニティを生成する際に、登録されたコンテンツリゾルバーを繰り返し処理し、そのオポチュニティを解決できるコンテンツリゾルバーを探します。 最初に戻る `true` が選択され、オポチュニティが解決されます。 可能なコンテンツリゾルバーがない場合は、そのオポチュニティはスキップされます。 通常、コンテンツ解決プロセスは非同期なので、コンテンツリゾルバーは TVSDK にプロセスが完了したことを通知します。

1. 独自のカスタムの実装 `ContentFactory`を拡張して、 `ContentFactory` インターフェイスと上書き `retrieveResolvers`.

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

1. を登録します。 `ContentFactory` から `MediaPlayer`.

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

1. パス： `AdvertisingMetadata` オブジェクトを TVSDK に次のように追加します。
   1. の作成 `AdvertisingMetadata` オブジェクト。
   1. を保存します。 `AdvertisingMetadata` ～に対して `MediaPlayerItemConfig`.

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. を拡張するカスタム広告リゾルバークラスの作成 `ContentResolver` クラス。
   1. カスタム広告リゾルバーで、 `doConfigure`, `doCanResolve`, `doResolve`, `doCleanup`:

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      お客様の `advertisingMetadata` 渡された項目から `doConfigure`:

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. 配置オポチュニティごとに、 `List<TimelineOperation>`.

      このサンプル `TimelineOperation` ～の構造を提供する `AdBreakPlacement`:

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. 広告が解決されたら、次のいずれかの関数を呼び出します。

      * 広告の解決に成功した場合は、を呼び出します。 `process(List<TimelineOperation> proposals)` および `notifyCompleted(Opportunity opportunity)` の `ContentResolverClient`

        ```java
        _client.process(timelineOperations); 
        _client.notifyCompleted(opportunity); 
        ```

      * 広告の解決に失敗した場合は、を呼び出します。 `notifyResolveError` の `ContentResolverClient`

        ```java
        _client.notifyFailed(Opportunity opportunity, PSDKErrorCode error);
        ```

        例：

        ```java
        _client.notifyFailed(opportunity, UNSUPPORTED_OPERATION);
        ```

<!--<a id="example_463B718749504A978F0B887786844C39"></a>-->

このサンプルのカスタム広告リゾルバーは、オポチュニティを解決し、シンプルな広告を提供します。

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
