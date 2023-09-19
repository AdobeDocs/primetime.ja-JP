---
description: インターフェイス PlacementOpportunityDetector を実装することで、独自のオポチュニティディテクターを実装できます。
title: カスタムオポチュニティディテクターの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# カスタムオポチュニティディテクターの実装 {#implement-a-custom-opportunity-detector}

インターフェイス PlacementOpportunityDetector を実装することで、独自のオポチュニティディテクターを実装できます。

1. カスタムの作成 `AdvertisingFactory` インスタンスとオーバーライド `createOpportunityDetector`. 例：

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

1. 広告クライアントファクトリをに登録します。 `MediaPlayer`. 例：

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. カスタムオポチュニティディテクタークラスを作成し、 `PlacementOpportunityDetector` クラス。
   1. カスタムオポチュニティディテクターで、この関数を上書きします。

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      The `timedMetadataList` 使用可能な `TimedMetadata`：並べ替えられます。 メタデータには、広告プロバイダーに送信されるターゲティングパラメーターとカスタムパラメーターが含まれます。

   1. 次ごとに `TimedMetadata`、 `List<PlacementOpportunity>`. リストは空にできますが、null はできません。 `PlacementOpportunity` は、次の属性を持つ必要があります。

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. 検出されたすべての時間指定メタデータオブジェクトに対して配置オポチュニティが作成されたら、単に `PlacementOpportunity` リスト。

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
