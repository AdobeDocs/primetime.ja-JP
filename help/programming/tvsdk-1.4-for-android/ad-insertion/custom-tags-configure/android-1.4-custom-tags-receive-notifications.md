---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。
title: 時間指定メタデータ追加通知のリスナー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# 時間指定メタデ追加ータ通知のリスナー{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。

関連するアクティビティをアプリケーションに通知する次のイベントをリッスンすると、時間指定メタデータを監視できます。

* `onTimedMetadata`:TVSDKは、コンテンツの解析中に一意のサブスクライブ済みタグを識別するたびに、新しい `TimedMetadata` オブジェクトを準備し、このイベントをディスパッチします。

   このオブジェクトには、サブスクライブしたタグの名前、このタグが表示される再生中のローカル時間、その他のデータが含まれます。

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

ID3メタデータは、同じonTimedMetadataリスナーを使用して、ID3タグの存在を示します。 ただし、`TimedMetadata`オブジェクトの`type`プロパティを使用してTAGとID3を区別できるので、混乱の原因になりません。 ID3タグについて詳しくは、[ID3タグ](../../../tvsdk-1.4-for-android/notification-system/android-1.4-id3-metadata-retrieve.md)を参照してください。
