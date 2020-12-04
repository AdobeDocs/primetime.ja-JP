---
description: 現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。
seo-description: 現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。
seo-title: 時間指定メタデータの使用
title: 時間指定メタデータの使用
uuid: 98bb8c08-2794-42d6-b5c3-b1047ac804fe
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# 時間指定メタデータを使用{#use-timed-metadata}

現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。

再生中にこれらの保存した`TimedMetadata`オブジェクトを使用するには、[Store timed-metadataオブジェクトをディスパッチ](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md)の`ArrayList`から使用して、保存した&lt;a1/>を使用します。

1. タイマーを実行し、現在の再生時間を繰り返しクエリします。
1. 現在の再生時間と一致する開始時間を持つすべての`TimedMetadata`オブジェクトを探します。

   これらのオブジェクトを使用して、様々なアクションを実行できます。

   >[!IMPORTANT]
   >
   >現在の再生時間が`TimedMetadata`オブジェクトと一致するかどうかをチェックする場合は、`shouldTriggerSubscribedTagEvent`を条件として含めます。

   様々な広告動作の結果として、タイムラインが変更される場合があります。 例えば、1つ以上の広告の時間がタイムライン上の元の位置から移動される場合がありますが、`shouldTriggerSubscribedTagEvent`は、`TimeMetadata`オブジェクトの開始時間が現在の再生時間と一致するようにします。

   例：

   ```java
    _playbackClockEventListener = new Clock.ClockEventListener() {
       @Override
       public void onTick(String name) {
           getActivity().runOnUiThread(new Runnable() {
               @Override
               public void run() {
                   /* handle timedmetadata object list  */ 
                   if (_mediaPlayer != null && _timedMetadataList != null && _timedMetadataList.size() > 0) {
                       if (_lastKnownStatus == MediaPlayer.PlayerState.PLAYING) {
                           long localTime = _mediaPlayer.getLocalTime();
                           Iterator<TimedMetadata> iterator = _timedMetadataList.iterator(); 
                           while (iterator.hasNext()) {
                               TimedMetadata timedMetadata = iterator.next();
                               long diff = localTime - timedMetadata.getTime();
                               if (diff >= 0 &&
                                   diff <= PLAYBACK_CLOCK_INTERVAL &&
                                   _mediaPlayer.shouldTriggerSubscribedTagEvent()) {
                                   // use timed metadata object
                               }
                           }
                       }
                   }
               }
           });
       }
   };
   _playbackClock.addClockEventListener(_playbackClockEventListener);
   ```

1. リストから古い`TimedMetadata`インスタンスを定期的にフラッシュして、メモリが継続的に増大するのを防ぎます。