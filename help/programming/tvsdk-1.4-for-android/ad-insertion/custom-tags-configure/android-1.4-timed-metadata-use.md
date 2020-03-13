---
description: 現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。
seo-description: 現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。
seo-title: 時間指定メタデータの使用
title: 時間指定メタデータの使用
uuid: 98bb8c08-2794-42d6-b5c3-b1047ac804fe
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 時間指定メタデータの使用 {#use-timed-metadata}

現在の再生時間が開始時間と一致する場合は、TimedMetadataを使用できます。

再生中にこれらの保存されたオ `TimedMetadata` ブジェクトを使用するには、 `ArrayList` Storeの時間指定メタデータオブジェクトをディスパッチ時に使用します [](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md)。

1. タイマーを実行し、現在の再生時間を繰り返しクエリします。
1. 現在の再生時間と一 `TimedMetadata` 致する開始時間を持つすべてのオブジェクトを検索します。

   これらのオブジェクトを使用して、様々なアクションを実行できます。

[!IMPORTANT]
現在の再生時間がオブジェクトと一致するかどうかをチェッ `TimedMetadata` クする場合は、を条件 `shouldTriggerSubscribedTagEvent` として含めます。

様々な広告動作の結果、タイムラインが変わる場合があります。 例えば、1つ以上の広告の時間がタイムライン上の元の位置から移動される場合がありますが、オブジェクトの開始時間は `shouldTriggerSubscribedTagEvent` 現在の再生時間と `TimeMetadata` 一致するようにする必要があります。

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

1. リストから古いインスタ `TimedMetadata` ンスを定期的にフラッシュし、メモリが継続的に増加するのを防ぎます。