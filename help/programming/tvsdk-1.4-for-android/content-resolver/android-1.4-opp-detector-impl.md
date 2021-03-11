---
description: PlacementOpportunityDetectorインターフェイスを実装することで、独自のオポチュニティディテクターを実装できます。
title: カスタムオポチュニティディテクターの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---


# カスタムオポチュニティディテクターの実装{#implement-a-custom-opportunity-detector}

PlacementOpportunityDetectorインターフェイスを実装することで、独自のオポチュニティディテクターを実装できます。

1. カスタム`AdvertisingFactory`インスタンスを作成し、`createOpportunityDetector`をオーバーライドします。 例：

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

1. 広告クライアントファクトリを`MediaPlayer`に登録します。 例：

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. `PlacementOpportunityDetector`クラスを拡張するカスタムオポチュニティディテクタークラスを作成します。
   1. カスタムオポチュニティディテクターで、次の関数を上書きします。

      ```java
      public List<PlacementOpportunity> process(List<TimedMetadata> timedMetadataList, Metadata metadata)
      ```

      `timedMetadataList`には、使用可能な`TimedMetadata`のリストが含まれており、これは並べ替えられます。 メタデータには、広告プロバイダーに送信されるターゲットパラメーターとカスタムパラメーターが含まれます。

   1. `TimedMetadata`ごとに、`List<PlacementOpportunity>`を作成します。 リストは空にできますが、nullは指定できません。 `PlacementOpportunity` には次の属性が必要です。

      ```java
      PlacementOpportunity( 
          String id,                                      // can be id from timedMetadata 
          PlacementInformation placementInformation   // PlacementInformation object containing Type, time, duration 
          Metadata metadata                           // ad metadata containing targeting params sent to the ad provider 
      )
      ```

   1. 検出されたすべての時間指定メタデータオブジェクトに対して配置オポチュニティが作成されたら、`PlacementOpportunity`リストを返します。

次に、カスタム配置オポチュニティディテクターのサンプルを示します。

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

