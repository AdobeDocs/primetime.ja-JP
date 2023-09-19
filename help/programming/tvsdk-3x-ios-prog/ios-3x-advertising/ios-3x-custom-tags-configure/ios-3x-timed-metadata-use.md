---
description: 現在の再生時間が開始時間と一致する場合は、 TimedMetadata を使用できます。
title: 時間指定メタデータを使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# 時間指定メタデータを使用 {#use-timed-metadata}

現在の再生時間が開始時間と一致する場合は、 TimedMetadata を使用できます。

これらを保存して使用するには `PTTimedMetadata` オブジェクトを再生中に、次の場所から保存したディクショナリを使用します。 [ディスパッチされる時間指定メタデータオブジェクトを保存します。](../../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-timed-metadata-store.md).

1. この通知から現在の再生時間を抽出して更新し、 `PTTimedMetadata` 現在の再生時間に一致する開始時間を持つオブジェクト。

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

1. 古いものを定期的にフラッシュ `PTTimedMetadata` インスタンスをリストから削除して、メモリが継続的に増大するのを防ぎます。
