---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
title: カスタムコンテンツリゾルバーの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# カスタムコンテンツリゾルバーの実装 {#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

TVSDK は、新しいオポチュニティを検出すると、登録されたコンテンツリゾルバーを繰り返し処理して、そのオポチュニティを解決できるコンテンツリゾルバーを探します。 オポチュニティの解決のために、最初に true を返したものが選択されます。 可能なコンテンツリゾルバーがない場合は、そのオポチュニティはスキップされます。 通常、コンテンツ解決プロセスは非同期なので、コンテンツリゾルバーはプロセスが完了したことを通知する役割を果たします。

1. カスタムの作成 `AdvertisingFactory` インスタンスとオーバーライド `createContentResolver`.

   例：

   ```java
   new AdvertisingFactory() { 
       ... 
       @Override 
       public ContentResolver createContentResolver(MediaPlayerItem item) { 
           Metadata metadata = _mediaPlayer.getCurrentItem().getResource().getMetadata(); 
           if (metadata != null) { 
               if (metadata.containsKey(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue())) { 
                   return new AuditudeResolver(getActivity().getApplicationContext()); 
               } else if (metadata.containsKey(DefaultMetadataKeys.JSON_METADATA_KEY.getValue())) { 
                   return new MetadataResolver(); 
               } else if (metadata.containsKey(DefaultMetadataKeys.TIME_RANGES_METADATA_KEY.getValue())) { 
                   return new CustomAdMarkersContentResolver(); 
               } else if (metadata.containsKey(CustomAdResolver.CUSTOM_METADATA_KEY)) { 
                   return new CustomAdResolver(); 
               } 
           } 
           return null; 
       } 
       ... 
   }
   ```

1. 広告クライアントファクトリをに登録します。 `MediaPlayer`.

   例：

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. パス： `AdvertisingMetadata` オブジェクトを TVSDK に次のように追加します。
   1. の作成 `AdvertisingMetadata` オブジェクトと `MetadataNode` オブジェクト。
   1. を保存します。 `AdvertisingMetadata` ～に対して `MetadataNode`.

   ```java
   MetadataNode result = new MetadataNode(); 
   result.setNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue(),  
                  advertisingMetadata);
   ```

1. を拡張するカスタム広告リゾルバークラスの作成 `ContentResolver` クラス。
   1. カスタム広告リゾルバーで、次の保護された関数を上書きします。

      ```java
      void doResolveAds(Metadata metadata,  
                        PlacementOpportunity placementOpportunity)
      ```

      メタデータには `AdvertisingMetada`. 次の場合に使用します。 `TimelineOperation` ベクトル生成。

   1. 配置オポチュニティごとに、 `Vector<TimelineOperation>`.

      ベクトルは空にすることができますが、null はできません。

      このサンプル `TimelineOperation` ～の構造を提供する `AdBreakPlacement`:

      ```java
      AdBreakPlacement(AdBreak.createAdBreak( 
                                ads,       // Vector<Ad> 
                                time,      // Ad Break start time. Note: local time on the timeline 
                                duration,  // Ad Break duration 
                                tag()      // An arbitrary string value that can be attached to  
                                           // the AdBreak object. 
                               ), placementInformation  // Retrieved from PlacementOpportunity 
      )
      ```

   1. 広告が解決されたら、次のいずれかの関数を呼び出します。

      * 広告の解決が成功した場合： `notifyResolveComplete(Vector<TimelineOperation> proposals)`
      * 広告の解決に失敗した場合： `notifyResolveError(Error error)`

      例えば、失敗した場合は次のようになります。

      ```java
      Metadata metadata = new MetadataNode(); 
      metadata.setValue("NATIVE_ERROR_CODE", exception.getCause().toString()); 
      error.setMetadata(metadata);
      ```

<!--<a id="example_4F0D7692A92E480A835D6FDBEDBE75E7"></a>-->

このサンプルのカスタム広告リゾルバーは、広告サーバーに対して HTTP リクエストを実行し、JSON 応答を受け取ります。

```java
public class CustomAdResolver extends ContentResolver { 
    ... 
    @Override 
    protected void doResolveAds(Metadata metadata, PlacementOpportunity placementOpportunity) { 
        ... 
        if (resolveSuccess == true) { 
            notifyResolveComplete(Vector<TimelineOperation> proposals); 
        } 
        else { 
            notifyResolveError(Error error); 
        } 
    } 
    ... 
}
```

ライブストリームに対する JSON 広告サーバーのレスポンスのサンプル：

```
{     
    "response": { 
        "breaks": [ { 
            "start": 0, 
            "ads": [ { 
                "id": 1001, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/geico/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset1", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } 
        ] }, 
        { 
            "start": -1, 
            "ads": [ { 
                "id": 1003, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/priceline/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset3", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        } ] 
    } 
} 
```

VOD に対する JSON 広告サーバーの応答の例：

```
{     
    "response": { 
        "breaks": [ { 
            "start": 0, 
            "ads": [ { 
                "id": 1001, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/geico/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset1", 
                    "resource_type": "" 
                }, 
                "companion_assets": {  
                } 
            }, 
            { 
                "id": 1002, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/crescent/playlist.m3u8", 
                    "duration": 15000, 
                    "id": "asset2", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        }, 
        { 
            "start": 50000, 
            "ads": [ { 
                "id": 1003, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/priceline/playlist.m3u8", 
                    "duration": 30000, 
                    "id": "asset3", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        }, 
        { 
            "start": 100000000, 
            "ads": [ { 
                "id": 1004, 
                "primary_asset": { 
                    "url": "https://venkat-test.s3.amazonaws.com/ads/camry/playlist.m3u8", 
                    "duration": 15000, 
                    "id": "asset4", 
                    "resource_type": "" 
                }, 
                "companion_assets": { 
                } 
            } ] 
        } ] 
    } 
} 
```
