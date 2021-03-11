---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
title: カスタムコンテンツリゾルバーの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 2%

---


# カスタムコンテンツリゾルバーの実装{#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

TVSDKは、新しいオポチュニティを生成する際に、登録されているコンテンツリゾルバーを繰り返し処理し、そのオポチュニティを解決できるコンテンツリゾルバーを探します。 オポチュニティの解決のために、`true`を最初に返すものが選択されます。 オポチュニティを解決できるコンテンツリゾルバーがない場合、そのオポチュニティはスキップされます。 通常、コンテンツ解決プロセスは非同期的なので、コンテンツリゾルバーは、TVSDKにプロセスが完了したことを通知する必要があります。

1. `ContentFactory`インターフェイスを拡張し、`retrieveResolvers`をオーバーライドして、独自のカスタム`ContentFactory`を実装します。

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

1. `ContentFactory`を`MediaPlayer`に登録します。

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

1. 次のように、`AdvertisingMetadata`オブジェクトをTVSDKに渡します。
   1. `AdvertisingMetadata`オブジェクトを作成します。
   1. `AdvertisingMetadata`オブジェクトを`MediaPlayerItemConfig`に保存します。

      ```java
      AdvertisingMetadata advertisingMetadata = new AdvertisingMetadata(); 
      
      advertisingMetadata.setDelayAdLoading(true); 
      ... 
      
      mediaPlayerItemConfig.setAdvertisingMetadata(advertisingMetadata); 
      ```

1. `ContentResolver`クラスを拡張するカスタム広告リゾルバークラスを作成します。
   1. カスタム広告リゾルバーで、`doConfigure`、`doCanResolve`、`doResolve`、`doCleanup`をオーバーライドします。

      ```java
      void doConfigure(MediaPlayerItem item); 
      boolean doCanResolve(Opportunity opportunity); 
      void doResolve(Opportunity opportunity); 
      void doCleanup();
      ```

      `doConfigure`に渡されたアイテムから`advertisingMetadata`を取得します。

      ```java
      MediaPlayerItemConfig itemConfig = item.getConfig(); 
      
      AdvertisingMetadata advertisingMetadata =  
        mediaPlayerItemConfig.getAdvertisingMetadata(); 
      ```

   1. 配置オポチュニティごとに、`List<TimelineOperation>`を作成します。

      次のサンプル`TimelineOperation`は`AdBreakPlacement`の構造を提供します。

      ```java
      AdBreakPlacement( 
          new AdBreak( ads,    // Vector<Ad> 
                       tracker // Content Tracker 
          ), 
          placementInformation // Retrieved from Opportunity 
      ); 
      ```

   1. 広告が解決されたら、次のいずれかの関数を呼び出します。

      * 広告の解決に成功した場合は、`ContentResolverClient`で`process(List<TimelineOperation> proposals)`と`notifyCompleted(Opportunity opportunity)`を呼び出します。

         ```java
         _client.process(timelineOperations); 
         _client.notifyCompleted(opportunity); 
         ```

      * 広告の解決に失敗した場合は、`ContentResolverClient`で`notifyResolveError`を呼び出します

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

