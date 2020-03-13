---
description: アプリケーションは、適切なPTTimedMetadataオブジェクトを適切なタイミングで使用する必要があります。
seo-description: アプリケーションは、適切なPTTimedMetadataオブジェクトを適切なタイミングで使用する必要があります。
seo-title: ディスパッチ時の時間指定メタデータオブジェクトの格納
title: ディスパッチ時の時間指定メタデータオブジェクトの格納
uuid: 38e72a9b-571a-48da-9c17-80be453e6a98
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# ディスパッチ時の時間指定メタデータオブジェクトの格納 {#store-timed-metadata-objects-as-they-are-dispatched}

アプリケーションは、適切なPTTimedMetadataオブジェクトを適切なタイミングで使用する必要があります。

再生前に発生するコンテンツの解析中に、TVSDKはサブスクライブされたタグを識別し、これらのタグをアプリケーションに通知します。 各時間に関連付けられる時間は、再 `PTTimedMetadata` 生タイムラインの絶対時間です。

アプリケーションは、次のタスクを実行する必要があります。

1. 現在の再生時間を追跡します。
1. 現在の再生時間を、ディスパッチされるオブジェクトに一致さ `PTTimedMetadata` せます。

1. 開始時間が `PTTimedMetadata` 現在の再生時間と等しい場所を使用します。

   >[!NOTE]
   >
   >以下のコードは、一度に1つのインスタンスしか存在しな `PTTimedMetadata` いことを前提としています。 複数のインスタンスがある場合、アプリケーションはそれらを適切に辞書に保存する必要があります。 1つの方法は、特定の時間に配列を作成し、その配列にすべてのインスタンスを格納することです。

   次の例は、各の開始時間でキ `PTTimedMetadata` ーを設定し `NSMutableDictionary (timedMetadataCollection)` たオブジェクトを保存する方法を示しま `timedMetadata`す。

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

## ニールセンID3タグの解析 {#example_3B51E9D4AF2449FAA8E804206F873ECF}

解析用にID3タグを抽出するには、次の方法を使用し `onMediaPlayerSubscribedTagIdentified` ます。

```
(void)onMediaPlayerSubscribedTagIdentified:(NSNotification *)notification 
{ 
NSDictionary *userInfo = [notification userInfo]; 
PTTimedMetadata *timedMetadata = (PTTimedMetadata *)[userInfo objectForKey:PTTimedMetadataKey]; 
if (timedMetadata.type == PTTimedMetadataTypeID3) 
Unknown macro: { PTMetadata *metadata = (PTMetadata *)timedMetadata; NSString * nstr = [[NSString alloc] initWithFormat} 
 
}
```

ID3タグを解析した後、次を使用して、ニールセン固有のメタデータを抽出します。

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
