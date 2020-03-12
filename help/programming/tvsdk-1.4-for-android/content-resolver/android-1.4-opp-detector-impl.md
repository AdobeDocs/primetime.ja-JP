---
description: PlacementOpportunityDetectorインターフェイスを実装することで、独自のオポチュニティディテクターを実装できます。
seo-description: PlacementOpportunityDetectorインターフェイスを実装することで、独自のオポチュニティディテクターを実装できます。
seo-title: カスタムオポチュニティディテクターの実装
title: カスタムオポチュニティディテクターの実装
uuid: 012527c5-4ef0-4cd6-a9df-2fb861078a7e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタムオポチュニティディテクターの実装 {#implement-a-custom-opportunity-detector}

PlacementOpportunityDetectorインターフェイスを実装することで、独自のオポチュニティディテクターを実装できます。

1. カスタムインスタンスを作 `AdvertisingFactory` 成し、上書きしま `createOpportunityDetector`す。 例：

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public PlacementOpportunityDetector createOpportunityDetector(MediaPlayerItem item) { 
           return new CustomPlacementOpportunityDetector(); 
       } 
       ... 
   }
   ```

1. に広告クライアントファクトリを登録しま `MediaPlayer`す。 例：

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. クラスを拡張するカスタムオポチュニティディテクタークラスを作成 `PlacementOpportunityDetector` します。
   1. カスタムオポチュニティディテクターで、次の関数を上書きします。

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      には、使 `timedMetadataList` 用可能なリストが含まれ、ソ `TimedMetadata`ートされています。 メタデータには、広告プロバイダーに送信されるターゲットパラメーターとカスタムパラメーターが含まれます。

   1. それぞれに対し `TimedMetadata`て、を作成しま `List<PlacementOpportunity>`す。 リストは空にできますが、nullはできません。 `PlacementOpportunity` には、次の属性が必要です。

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. 検出されたすべての時間指定メタデータオブジェクトに対して配置オポチュニティが作成されたら、リストを返 `PlacementOpportunity` します。

次に、カスタム配置オポチュニティディテクターの例を示します。

```java
public class CustomPlacementOpportunityDetector implements PlacementOpportunityDetector { 
    ... 
    @Override 
    public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata) { 
        ... 
        List<PlacementOpportunity> opportunities = new ArrayList<PlacementOpportunity>(); 
 
        for (TimedMetadata timedMetadata : timedMetadataList) { 
 
            if (isOpportunity(timedMetadata)) {        // check if given timedMetadata should be  
                                                       // considered as an opportunity 
 
                // create an object of PlacementOpportunity and add it to the opportunities list 
                PlacementOpportunity opportunity =  
                  createPlacementOpportunity(timedMetadata, airingId, metadata); 
                Opportunities.add(opportunity); 
            } 
        } 
        return opportunities; 
    }    
    ... 
} 
```

