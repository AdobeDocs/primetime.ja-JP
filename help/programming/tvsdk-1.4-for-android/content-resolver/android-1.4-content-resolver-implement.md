---
description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
seo-description: デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。
seo-title: カスタムコンテンツリゾルバーの実装
title: カスタムコンテンツリゾルバーの実装
uuid: 88627fdc-3b68-4a9f-847e-a490ea8e3034
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタムコンテンツリゾルバーの実装 {#implement-a-custom-content-resolver}

デフォルトのリゾルバーに基づいて、独自のコンテンツリゾルバーを実装できます。

TVSDKは、新しいオポチュニティを検出すると、登録されたコンテンツリゾルバーを繰り返し処理し、そのオポチュニティを解決できるコンテンツリゾルバーを探します。 trueを最初に返したものが、オポチュニティの解決に選択されます。 使用できるコンテンツリゾルバーがない場合、そのオポチュニティはスキップされます。 コンテンツ解決プロセスは通常非同期なので、コンテンツリゾルバーは、プロセスが完了したことを通知します。

1. カスタムインスタンスを作 `AdvertisingFactory` 成し、上書きしま `createContentResolver`す。

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

1. に広告クライアントファクトリを登録しま `MediaPlayer`す。

   例：

   ```java
   // register the custom advertising factory with media player 
   advertisingFactory = createCustomAdvertisingFactory(); 
   mediaPlayer.registerAdClientFactory(advertisingFactory);
   ```

1. 次の手順でTVSDK `AdvertisingMetadata` にオブジェクトを渡します。
   1. オブジェクトとオ `AdvertisingMetadata` ブジェクトを作 `MetadataNode` 成します。
   1. オブジェクトを `AdvertisingMetadata` に保存しま `MetadataNode`す。

   ```java
   MetadataNode result = new MetadataNode(); 
   result.setNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue(),  
                  advertisingMetadata);
   ```

1. クラスを拡張するカスタム広告リゾルバークラスを作成 `ContentResolver` します。
   1. カスタム広告リゾルバーで、次の保護された関数を上書きします。

      ```java
      void doResolveAds(Metadata metadata,  
                        PlacementOpportunity placementOpportunity)
      ```

      メタデータにはユーザが含まれてい `AdvertisingMetada`ます。 次のベクトル生成に使 `TimelineOperation` 用します。

   1. 配置オポチュニティごとに、を作成しま `Vector<TimelineOperation>`す。

      ベクトルは空にできますが、nullは指定できません。

      このサンプル `TimelineOperation` は、次の構造を提供しま `AdBreakPlacement`す。

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

      * 広告の解決に成功した場合： `notifyResolveComplete(Vector<TimelineOperation> proposals)`
      * 広告の解決に失敗した場合： `notifyResolveError(Error error)`
      例えば、失敗した場合は次のようになります。

      ```java
      Metadata metadata = new MetadataNode(); 
      metadata.setValue("NATIVE_ERROR_CODE", exception.getCause().toString()); 
      error.setMetadata(metadata);
      ```


<!--<a id="example_4F0D7692A92E480A835D6FDBEDBE75E7"></a>-->

このサンプルのカスタム広告リゾルバーは、広告サーバーにHTTPリクエストを送信し、JSON応答を受け取ります。

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

ライブストリームに対するJSON広告サーバーの応答の例：

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

VODに対するJSON広告サーバーの応答の例：

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

