---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。
seo-description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。
seo-title: 時間指定メタデータ通知のリスナーの追加
title: 時間指定メタデータ通知のリスナーの追加
uuid: bb996b4a-282e-4321-a9e9-513f0df45b70
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# 時間指定メタデータ通知のリスナーの追加 {#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。

時間指定メタデータを監視するには、をリッスンし、関連するア `onTimedMetadata`クティビティをアプリケーションに通知します。 コンテンツの解析中に一意のサブスクライブ済みタグが識別されるたびに、TVSDKは新しいオブジェクトを準備し、こ `TimedMetadata` のイベントをディスパッチします。 このオブジェクトには、サブスクライブしたタグの名前、このタグが表示される再生時のローカル時間、その他のデータが含まれます。

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

ID3メタデータは、同じリス `onTimedMetadata` ナーを使用してID3タグの存在を示します。 ただし、このプロパティを使用してTAGとID3を区別できるので、 `TimedMetadata``type` 混乱の原因になることはありません。 ID3タグについて詳しくは、 [ID3タグを参照してください](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md)。