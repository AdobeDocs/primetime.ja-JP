---
description: アプリケーションでは、適切な PTTimedMetadata オブジェクトを適切なときに使用する必要があります。
title: ディスパッチされる時間指定メタデータオブジェクトを保存します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# ディスパッチされる時間指定メタデータオブジェクトを保存します {#store-timed-metadata-objects-as-they-are-dispatched}

アプリケーションでは、適切な PTTimedMetadata オブジェクトを適切なときに使用する必要があります。

再生前に発生するコンテンツ解析中に、 TVSDK はサブスクライブされているタグを識別し、これらのタグに関してアプリケーションに通知します。 各 `PTTimedMetadata` は、再生タイムラインでの絶対時間です。

アプリケーションは、次のタスクを実行する必要があります。

1. 現在の再生時間を追跡します。
1. 現在の再生時間とディスパッチ済みの時間を一致させる `PTTimedMetadata` オブジェクト。

1. 以下を使用します。 `PTTimedMetadata` ここで、開始時間は現在の再生時間と等しくなります。

   >[!NOTE]
   >
   >以下のコードは、が 1 つのみであることを前提としています。 `PTTimedMetadata` インスタンスを一度に作成します。 複数のインスタンスが存在する場合、アプリケーションはそれらを辞書に適切に保存する必要があります。 1 つの方法は、特定の時間に配列を作成し、すべてのインスタンスをその配列に格納することです。

   次の例は、 `PTTimedMetadata` 内のオブジェクト `NSMutableDictionary (timedMetadataCollection)` 各 `timedMetadata`.

   ```
   NSMutableDictionary *timedMetadataCollection; 
   
   - (void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
   { 
       if (!timedMetadataCollection) 
       { 
           timedMetadataCollection = [[NSMutableDictionary alloc] init]; 
       } 
       NSDictionary *userInfo = [notification userInfo]; 
       PTTimedMetadata *timedMetadata = [(PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey] retain]; 
       if ([timedMetadata.name  isEqualToString: @"#EXT-OATCLS-SCTE35"]) 
       { 
            NSLog(@"Adding timedMetadata %@ to timedMetadataCollection with time                      
                    %f",timedMetadata.name,CMTimeGetSeconds(timedMetadata.time)); 
   
           NSNumber *timedMetadataStartTime = [NSNumber numberWithInt:(int)CMTimeGetSeconds(timedMetadata.time)]; 
           [timedMetadataCollection setObject:timedMetadata forKey:timedMetadataStartTime]; 
       } 
       [timedMetadata release]; 
   }
   ```

## Nielsen ID3 タグの解析 {#example_3B51E9D4AF2449FAA8E804206F873ECF}

解析用に ID3 タグを抽出するには、次のコードを `onMediaPlayerSubscribedTagIdentified` メソッド：

```
(void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
{ 
NSDictionary *userInfo = [notification userInfo]; 
PTTimedMetadata *timedMetadata = (PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey]; 
if (timedMetadata.type == PTTimedMetadataTypeID3) 
Unknown macro: { PTMetadata *metadata = (PTMetadata *)timedMetadata; NSString * nstr = [[NSString alloc] initWithFormat} 
 
}
```

ID3 タグを解析した後、次のコードを使用して Nielsen 固有のメタデータを抽出します。

```
    (NSString *)parseNielsenUrlFromID3Tag:(NSString *)str 
    { 
    /* ID3 tag <AVMetadataItem: 0x15e58e60, identifier=id3/PRIV, keySpace=org.id3, key class = __NSCFString, key=PRIV, commonKey=(null), extendedLanguageTag=(null), dataType=(null), time= {110265598/4410000 = 25.004} 
 
    , duration= 
    {INVALID} 
 
    , startDate=(null), extras= 
    { info = "www.nielsen.com/X100zdCIGeIlgZnkYj6UvQ==/pI-X5FFk07770SXf2ZbI6g==/CE0C6​1TsDo0jIrNn9N2yTPe6nVG3dHZHfgS52fJeQjf9fJCga9tj4OW4NXPZ9fI1mx0gfYUPBXnjqolHemZPtn_FCoNg​8Dqw8-Auruf15fU04pJfXTTN0IgZ4iWBmeRiPpS9X100zdCIGeIlgZnkYj6UvVjmPIdY5jyRQTA=/00000/21778/00"; } 
 
    , value length=1> 
    */ 
 
NSString *nielsenStr = nil; 
for (NSString *keyValuePairString in [str componentsSeparatedByString:@", "]) 
{ 
if([keyValuePairString rangeOfString:@"nielsen.com"].location != NSNotFound) 
{ // Nielsen NSRange start = [keyValuePairString rangeOfString:@"\""]; NSRange end = [keyValuePairString rangeOfString:@"\";"]; nielsenStr = [keyValuePairString substringWithRange:NSMakeRange(start.location + 1, end.location-start.location)]; } 
 
} 
return nielsenStr; 
}
```
