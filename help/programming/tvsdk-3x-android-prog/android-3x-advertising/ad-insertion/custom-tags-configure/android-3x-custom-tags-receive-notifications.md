---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。
title: 時間指定メタデータ通知のリスナーを追加する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 時間指定メタデータ通知のリスナーを追加する {#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。

時間指定メタデータを監視するには、 `onTimedMetadata`：関連するアクティビティをアプリケーションに通知します。 コンテンツの解析中に一意のサブスクライブ済みタグが識別されるたびに、 TVSDK は新しい `TimedMetadata` オブジェクトを探し、このイベントをディスパッチします。 オブジェクトには、購読したタグの名前、このタグが表示される再生中のローカル時間、その他のデータが含まれます。

イベントをリッスンします。

```java
private final TimedMetadataEventListener timedMetadataEventListener = new TimedMetadataEventListener() { 
    @Override 
    public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { 
        TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata(); 
 
        TimedMetadata.Type type = timedMetadata.getType(); 
        if (type.equals(TimedMetadata.Type.ID3)){ 
            Metadata metadata = timedMetadata.getMetadata(); 
            Set<String> keys = metadata.keySet(); 
            for (String key : keys) { 
                String value = metadata.getValue(key); 
            } 
        } else if (_mediaPlayer.getPlaybackRange() != null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
            displayRanges(); 
        } 
    } 
}; 
```

ID3 メタデータは同じ値を使用します `onTimedMetadata` リスナーを使用して、ID3 タグの有無を示します。 ただし、 `TimedMetadata` `type` プロパティを使用して TAG と ID3 を区別します。 ID3 タグについて詳しくは、 [ID3 タグ](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md).
