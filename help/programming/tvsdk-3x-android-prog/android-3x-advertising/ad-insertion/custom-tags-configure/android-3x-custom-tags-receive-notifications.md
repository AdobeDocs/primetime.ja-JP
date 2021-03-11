---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。
title: 時間指定メタデータ追加通知のリスナー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# 時間指定メタデ追加ータ通知のリスナー{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装する必要があります。

`onTimedMetadata`をリッスンすると、時間指定メタデータを監視できます。これにより、関連するアクティビティがアプリケーションに通知されます。 TVSDKは、コンテンツの解析中に一意のサブスクライブ済みタグを識別するたびに、新しい`TimedMetadata`オブジェクトを準備し、このイベントをディスパッチします。 このオブジェクトには、サブスクライブしたタグの名前、このタグが表示される再生中のローカル時間、その他のデータが含まれます。

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

ID3メタデータは、同じ`onTimedMetadata`リスナーを使用してID3タグの存在を示します。 ただし、`TimedMetadata` `type`プロパティを使用してTAGとID3を区別できるので、混乱の原因になりません。 ID3タグについて詳しくは、[ID3タグ](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-id3-metadata-retrieve.md)を参照してください。