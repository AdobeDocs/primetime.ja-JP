---
description: 現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。
seo-description: 現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。
seo-title: 時間指定メタデータの使用
title: 時間指定メタデータの使用
uuid: 9bbdaefa-4ac5-4e08-92b4-15ebe5c46864
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# 時間指定メタデータの使用{#use-timed-metadata}

現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。

再生中にこれらの保存されたオ `PTTimedMetadata` ブジェクトを使用するには、ディスパッチされる [Store timed-metadataオブジェクトの保存済みディクショナリを使用します](../../../tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-timed-metadata-store.md)。

1. この通知から現在の再生時間を抽出して更新し、現在の再生時間と一致する開 `PTTimedMetadata` 始時間を持つすべてのオブジェクトを検索します。

   これらのオブジェクトを使用して、様々なアクションを実行できます。

   例：

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification 
   { 
       CMTimeRange seekableRange = self.player.seekableRange; 
       if (CMTIMERANGE_IS_VALID(seekableRange)) 
       { 
           int currentTime = (int) CMTimeGetSeconds(self.player.currentTime); 
           NSArray *allKeys = timedMetadataCollection ? [timedMetadataCollection allKeys] : [NSArray array]; 
           NSMutableArray *timedMetadatasToDelete = [[[NSMutableArray alloc] init] autorelease]; 
           int count = [allKeys count]; 
   
           for (int i=count - 1; i > -1; i--) 
           { 
              NSNumber *currTimedMetadataTime = allKeys[i]; 
              if ([currTimedMetadataTime integerValue] == currentTime) 
              { 
               /* 
                   Use the timed metadata here and remove it from the collection. 
               */ 
                NSLog (@"IN PLAYBACK TIME %i TO EXECUTE TIMEDMETADATA %@ scheduled at time %f",currentTime,currTimedMetadata.name,CMTimeGetSeconds(currTimedMetadata.time)); 
   
               PTTimedMetadata *currTimedMetadata = [timedMetadataCollection objectForKey:currTimedMetadataTime]; 
               [timedMetadatasToDelete addObject:currTimedMetadataTime]; 
              } 
           } 
   
           for (int i=0; i<[timedMetadatasToDelete count]; i++) 
           { 
               NSNumber *timedMetadataToDelete = timedMetadatasToDelete[i]; 
               [timedMetadataCollection removeObjectForKey:timedMetadataToDelete]; 
           } 
       } 
   }
   ```

1. リストから古いインスタ `PTTimedMetadata` ンスを定期的にフラッシュし、メモリが継続的に増加するのを防ぎます。
