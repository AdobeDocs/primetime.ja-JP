---
description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。
seo-description: マニフェスト内のタグに関する通知を受け取るには、適切なイベントリスナーを実装します。
seo-title: 時間指定メタデータ追加通知のリスナー
title: 時間指定メタデータ追加通知のリスナー
uuid: cd7a5936-d63a-4711-ac16-2d79bac099a3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '173'
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
