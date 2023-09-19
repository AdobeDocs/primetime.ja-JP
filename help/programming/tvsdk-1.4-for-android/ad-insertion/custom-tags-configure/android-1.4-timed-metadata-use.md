---
description: 現在の再生時間が開始時間と一致する場合は、 TimedMetadata を使用できます。
title: 時間指定メタデータを使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 時間指定メタデータを使用 {#use-timed-metadata}

現在の再生時間が開始時間と一致する場合は、 TimedMetadata を使用できます。

これらを保存して使用するには `TimedMetadata` 再生中のオブジェクトは、保存した `ArrayList` から [ディスパッチされる時間指定メタデータオブジェクトを保存します。](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. タイマーを実行し、現在の再生時間を繰り返し問い合わせます。
1. 次のすべてを検索： `TimedMetadata` 現在の再生時間に一致する開始時間を持つオブジェクト。

   これらのオブジェクトを使用して、様々なアクションを実行できます。

   >[!IMPORTANT]
   >
   >現在の再生時間がいずれかと一致するかどうかを確認する場合 `TimedMetadata` オブジェクト、含む `shouldTriggerSubscribedTagEvent` を条件として使用します。

   様々な広告動作の結果、タイムラインが変わる場合があります。 例えば、1 つ以上の広告の時間がタイムライン上の元の位置から移動される場合がありますが、 `shouldTriggerSubscribedTagEvent` 次のようにして `TimeMetadata` オブジェクトの開始時間は、現在の再生時間と一致します。

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

1. 古いものを定期的にフラッシュ `TimedMetadata` インスタンスをリストから削除して、メモリが継続的に増大するのを防ぎます。
