---
description: 既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（遅延広告解決はデフォルトで無効になっています）。
keywords: 遅延；広告解決；広告の読み込み；delayLoading
title: 遅延広告解決を有効にする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 遅延広告解決を有効にする {#enable-lazy-ad-resolving}

既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（遅延広告解決はデフォルトで無効になっています）。

遅延広告解決は、 [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) true または false を使用します。

* ブール値を使用 *hasDelayAdLoading* および *setDelayAdLoading* 広告解決のタイミングとタイムラインでの広告の配置を制御する AdvertisingMetadata のメソッド：

   * 次の場合 *hasDelayAdLoading* false を返す場合、 TVSDK は、すべての広告が解決され、配置されてから、PREPARED 状態に移行します。
   * 次の場合 *hasDelayAdLoading* true を返します。 TVSDK は、最初の広告とトランジションのみを PREPARED 状態に解決します。

      * 残りの広告は、再生中に解決され、配置されます。

   * When *hasPreroll *or *hasLivePreroll* false を返す場合、 TVSDK はプリロール広告がないと仮定し、コンテンツの再生を直ちに開始します。 これらはデフォルトで true に設定されています。

**遅延広告解決に関連する API:**

```
Class:    com.adobe.mediacore.metadata.AdvertisingMetadata 
Methods: 
    public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
    public final void setDelayAdLoading() // Enable or disable Lazy Ad Resolving 
    public final void setDelayAdLoadingTolerance() // Sets the Lazy Ad Resolving Tolerance level.  This value is added to the BufferControlParameters::playBufferTime and the content's EXT-X-TARGETDURATION to determine when ad breaks should resolve 
    public final double getDelayAdLoadingTolerance() // Gets the Lazy Ad Resolving Tolerance level 
    public final boolean hasPreroll() // Check for existence of pre-roll ads 
    public final void setPreroll() // Set pre-roll true or false 
    public final boolean hasLivePreroll() // Check for live pre-roll ads 
    public final void setLivePreroll() // Set live pre-roll true or false

Class:     com.adobe.mediacore.timeline.TimelineMarker 
Methods: 
    public double getDuration() // Returns the current duration of the TimelineMarker.  This will be zero if the ad break has not yet resolved. 
    public Placement.Type getPlacementType() // Returns whether
```

広告をスクラブバーのキューとして正確に反映させるには、 `TimelineEvent`イベントを受け取るたびに、スクラブバーを再描画してください。

VOD ストリームに対して遅延広告解決が有効になっている場合、すべての広告の時間はタイムラインに配置されますが、広告の時間の多くはまだ解決されていません。 これらのマーカーを描画するかどうかは、 `TimelineMarker::getDuration()`. 値が 0 より大きい場合、広告ブレーク内の広告が解決されています。

TVSDK は、広告の時間が解決されたときや、プレーヤーが PREPARED ステータスに移行したときにも、このイベントをディスパッチします。

```
mediaPlayer.addEventListener(MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
/** 
* ... 
*/ 
public void onTimelineUpdated(TimelineEvent event) { 
for (PlaybackManagerEventListener listener : eventListeners) { 
  listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
}
```
