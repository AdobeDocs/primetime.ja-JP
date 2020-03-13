---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。
seo-description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。
seo-title: 時間指定メタデータ通知のリスナーの追加
title: 時間指定メタデータ通知のリスナーの追加
uuid: cd7a5936-d63a-4711-ac16-2d79bac099a3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 時間指定メタデータ通知のリスナーの追加 {#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。

次のイベントをリッスンして、時間指定メタデータを監視できます。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `onTimedMetadata`:コンテンツの解析中に一意のサブスクライブ済みタグが識別されるたびに、TVSDKは新しいオブジェクトを準備し、こ `TimedMetadata` のイベントをディスパッチします。

   このオブジェクトには、サブスクライブしたタグの名前、このタグが表示される再生時のローカル時間、その他のデータが含まれます。

   イベントをリッスンします。

   ```java
   private final TimedMetadataEventListener timedMetadataEventListener =  
     new TimedMetadataEventListener() { 
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
           } else if (_mediaPlayer.getPlaybackRange() !=  
                      null && _mediaPlayer.getPlaybackRange().getDuration() > 0) { 
               displayRanges(); 
           } 
       } 
   }; 
   ```

ID3メタデータは、同じonTimedMetadataリスナーを使用してID3タグの存在を示します。 ただし、TAGとID3を区別するためにオブジェクトのプロパティを使 `TimedMetadata` 用できるので、 `type` 混乱の原因になることはありません。 ID3タグについて詳しくは、 [ID3タグを参照してください](../../../tvsdk-1.4-for-android/notification-system/android-1.4-id3-metadata-retrieve.md)。
