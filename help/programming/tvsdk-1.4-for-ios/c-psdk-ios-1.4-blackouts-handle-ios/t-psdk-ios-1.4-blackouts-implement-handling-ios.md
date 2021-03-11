---
description: TVSDKは、ブラックアウト期間を処理するためのAPIとサンプルコードを提供します。
title: ブラックアウト処理の実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 1%

---


# ブラックアウト処理{#implement-blackout-handling}を実装

TVSDKは、ブラックアウト期間を処理するためのAPIとサンプルコードを提供します。

ブラックアウト処理を実装し、ブラックアウト中に代替コンテンツを提供するには：

1. ライブストリームマニフェストのブラックアウトタグをサブスクライブするようにアプリを設定します。

```
 - (void) createMediaPlayer:(PTMediaPlayerItem *)item
 { 
     [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:<INSERT-BLACKOUT-TAG>]];
     // For example:  
     // [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-OATCLS-SCTE35"]];
 }
```

1. 追加`PTTimedMetadataChangedNotification`の通知リスナーです。

   ```
   - (void)addobservers 
   { 
       [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerSubscribedTagIdentified:)  
         name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
   }
   ```

1. フォアグラウンドで`PTTimedMetadata`オブジェクトのリスナーメソッドを実装します。

   例：

   ```
   - (void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
   { 
       NSDictionary *userInfo = [notification userInfo]; 
       PTTimedMetadata *timedMetadata = [(PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey]  
         retain]; 
   
    if ([timedMetadata.name isEqualToString:<INSERT-BLACKOUT-TAG>]) 
       { 
        // handle tag. For example: store it in a dictionary keyed by time to be handled when  
        //   playback time = timedMetadata time. 
           NSNumber *timedMetadataStartTime =  
             [NSNumber numberWithInt:(int)CMTimeGetSeconds(timedMetadata.time)]; 
           [timedMetadataCollection setObject:timedMetadata forKey:timedMetadataStartTime]; 
       } 
   
       [timedMetadata release]; 
   }
   ```

1. 再生中に一定の更新を行って`TimedMetadata`オブジェクトを処理します。

   ```
   - (void)onMediaPlayerTimeChange:(NSNotification *)notification 
   { 
       @synchronized(self) 
       { 
           CMTimeRange seekableRange = self.player.seekableRange; 
           if (CMTIMERANGE_IS_VALID(seekableRange)) 
           { 
               _currentTime = (int) CMTimeGetSeconds(self.player.currentTime); 
               if (isnan(_currentTime)) 
               { 
                   _currentTime = 0; 
               } 
               [self handleCollectionAtTime:_currentTime]; 
           } 
       } 
   }
   ```

1. 代替コンテンツに追加切り替え、`PTTimedMetadata`オブジェクトに示されるメインコンテンツとその再生時間に戻る`PTTimedMetadata`ハンドラー。

   ```
   - (void)handleCollectionAtTime:(int)currentTime 
   { 
       NSArray *allKeys = nil; 
       NSMutableArray * timedMetadatasToDelete = [[[NSMutableArray alloc]init]autorelease]; 
   
       if (!_inBlackout && timedMetadataCollection) 
       { 
           allKeys = [timedMetadataCollection allKeys]; 
           int count = [allKeys count]; 
           for (int i=count-1; i>-1; i--) 
           { 
               NSNumber *currTimedMetadataTime = allKeys[i]; 
               PTTimedMetadata *currTimedMetadata =  
                 [timedMetadataCollection objectForKey:currTimedMetadataTime]; 
   
               if (currentTime == [currTimedMetadataTime integerValue] &&  
                                  currTimedMetadata.name == <INSERT-BLACKOUT-TAG> &&  
                                  [self isBlackoutStart: currTimedMetadata]) 
               { 
                                   PTAdMetadata *newItemAdMetadata =  
                                     [self createAlternateMediaMetadata];            
   
               // 1. Turn off preroll on the alternate media item. 
                   newItemAdMetadata.enableLivePreroll = NO; 
   
                               PTMediaPlayerItem *newItem =  
                                 [[PTMediaPlayerItem alloc]initWithUrl: 
                                   <INSERT-ALTERNATE-STREAM-URL mediaId:<INSERT-ALTERNATE-STREAM- 
                                    MEDIA-ID> metadata:newItemAdMetadata];
   
              // 2. Register the current (original playback item) in background. 
                   [self.player registerCurrentItemAsBackgroundItem]; 
   
              // 3. Replace the current playback item with the alternate stream. 
                    [self.player replaceCurrentItemWithPlayerItem:newItem]; 
   
              // 4. Reset observers. 
                   [self removeObservers]; 
                   [self addobservers]; 
   
              // 5. Register listener on the subscribed tags in background item. 
                   [[NSNotificationCenter defaultCenter] addObserver:self  
                      selector:@selector(onSubscribedTagInBackground:)  
                       name:PTTimedMetadataChangedInBackgroundNotification  
                         object:self.player.currentItem]; 
   
              // 6. Register listener on the error in background item. 
                            [[NSNotificationCenter defaultCenter]  
                               addObserver:self selector:@selector(onBackgroundManifestError:)  
                               name:PTBackgroundManifestErrorNotification   
                                 object:self.player.currentItem]; 
   
              // 7. Resume playback 
                        [self.player play]; 
   
                       // 8. Set boolean to true to handle blackout end. 
                     _inBlackout = YES; 
                     break; 
               } 
           } 
       } 
       else if (_inBlackout && backgroundTimedMetadataCollection) 
       { 
           allKeys = [backgroundTimedMetadataCollection allKeys]; 
           int count = [allKeys count]; 
           for (int i=count-1; i>-1; i--) 
           { 
               NSNumber *currTimedMetadataTime = allKeys[i]; 
               PTTimedMetadata *currTimedMetadata =  
                 [backgroundTimedMetadataCollection objectForKey:allKeys[i]]; 
   
               if (currentTime == ([currTimedMetadataTime integerValue] &&  
                 currTimedMetadata.name == <INSERT-BLACKOUT-TAG>  &&  
                 [self isBlackoutEnd:currTimedMetadata] ) 
               {      
                                  // 1. Come out of blackout. Unregister background item. 
                              [self.player unregisterCurrenBackgroundItem]; 
   
                       PTMetadata *metadata = [self createMetadata]; 
                       PTAdMetadata *adMetadata =  
                         (PTAdMetadata *)[currMetadata metadataForKey:PTAdResolvingMetadataKey]; 
                             adMetadata.enableLivePreroll = NO; 
   
                               PTMediaPlayerItem *item =  
                                 [[[PTMediaPlayerItem alloc] initWithUrl:<INSERT-ORIGINAL-URL>  
                                   mediaId:<INSERT-ORIGINAL-MEDIAID> metadata:metadata autorelease]; 
   
                                   // 2. Switch back to original item. 
                       [self.player replaceCurrentItemWithPlayerItem:item]; 
                       self.player.autoPlay = YES; 
                       [self removeObservers]; 
   
                       // 3. Remove background item listener. 
                       [[NSNotificationCenter defaultCenter] removeObserver:self  
                          name:PTTimedMetadataChangedInBackgroundNotification  
                       object:self.player.currentItem]; 
   
                                  [[NSNotificationCenter defaultCenter] removeObserver:self  
                                     name:PTBackgroundManifestErrorNotification 
                       object:self.player.currentItem]; 
                       [self addobservers]; 
                       [self.player play]; 
   
                               // 4. Update boolean to correctly maintain the current state. 
                       _inBlackout = NO; 
                       break; 
               } 
           } 
       } 
   }
   ```

1. バックグラウンドで`PTTimedMetadata`オブジェクトのリスナーメソッドを実装します。

   ```
   - (void)onSubscribedTagInBackground:(NSNotification *)notification 
   { 
       NSDictionary *userInfo = [notification userInfo]; 
       PTTimedMetadata *timedMetadata = [(PTTimedMetadata *) 
         [userInfo objectForKey:PTTimedMetadataKey] retain]; 
   
       if ([timedMetadata.name isEqualToString:<INSERT-BLACKOUT-TAG>]) 
       { 
           NSNumber *timedMetadataStartTime =  
             [NSNumber numberWithInt:(int)CMTimeGetSeconds(timedMetadata.time)]; 
           [backgroundTimedMetadataCollection  
              setObject:timedMetadata forKey:timedMetadataStartTime]; 
       } 
   
       [timedMetadata release]; 
   }
   ```

1. バックグラウンドエラーのリスナーメソッドを実装します。

   ```
   - (void) onBackgroundManifestError:(NSNotification *)notification 
   { 
       NSLog (@"onBackgroundManifestError"); 
   }
   ```

1. ブラックアウト範囲が再生ストリームのDVR上にある場合は、シーク不可能範囲を更新します。

   ```
   // This sample assumes that blackoutStartTimedMetadata is the PTTimedMetadata  
   // object that indicated "blackout start", and assuming blackoutEndTimedMetadata is the  
   // PTTimedMetadataObject that indicated "blackout end". Since in this case they are both  
   // in DVR, both are notified to the application before playback starts. This is the right  
   // time for the application to set this range in DVR as non-seekable range. 
   
   CMTime ignoreRangeStart = blackoutStartTimedMetadata.time; 
   CMTime ignoreRangeDuration = CMTimeMakeWithSeconds(CMTimeMakeWithSeconds  
     (CMTimeGetSeconds(blackoutEndTimedMetadata.time) -   
        CMTimeGetSeconds(blackoutStartTimedMetadata.time)),  
          blackoutEndTimedMetadata.time.timescale); 
   
   CMTimeRange ignoreRange = CMTimeRangeMake(ignoreRangeStart, ignoreRangeDuration); 
   NSArray *ignoreRangeArray = [NSArray arrayWithObject:[NSValue valueWithCMTimeRange:ignoreRange]]; 
   PTBlackoutMetadata *blackoutMetadata =  
     [[PTBlackoutMetadata alloc]initWithNonSeekableRanges:ignoreRangeArray]; 
   PTMetadata *currMetadata = self.item.metadata; 
   
   if (currMetadata) 
   { 
       [currMetadata setMetadata:blackoutMetadata forKey:PTBlackoutMetadataKey] 
   }
   ```
