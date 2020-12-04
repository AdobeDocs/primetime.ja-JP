---
description: 遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（遅延広告解決はデフォルトで無効です）。
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: 遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（遅延広告解決はデフォルトで無効です）。
seo-title: 遅延広告解決の有効化
title: 遅延広告解決の有効化
uuid: 91884eea-a622-4f5d-b6a8-36bb0050ba1d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---


# 遅延広告解決を有効にする{#enable-lazy-ad-resolving}

遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（遅延広告解決はデフォルトで無効です）。

遅延広告解決を有効または無効にするには、[AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-)をtrueまたはfalseで呼び出します。

* 広告解決のタイミングと広告のタイムライン上の配置を制御するには、AdvertisingMetadataでブール値&#x200B;*hasDelayAdLoading*&#x200B;メソッドと&#x200B;*setDelayAdLoading*&#x200B;メソッドを使用します。

   * *hasDelayAdLoading*&#x200B;がfalseを返す場合、TVSDKは、すべての広告が解決され、配置されてから、PREPARED状態に移行します。
   * *hasDelayAdLoading*&#x200B;がtrueを返した場合、TVSDKは、最初の広告とトランジションのみをPREPARED状態に解決します。

      * 残りの広告は再生中に解決され、配置されます。
   * *hasPreroll *または&#x200B;*hasLivePreroll*&#x200B;がfalseを返した場合、TVSDKは、プリロール広告がないと見なし、コンテンツの直ちに再生を開始します。 これらはデフォルトでtrueに設定されています。


**遅延広告解決に関連するAPI:**

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

広告をスクラブバーのキューとして正確に反映させるには、`TimelineEvent`イベントをリッスンし、このイベントを受け取るたびにスクラブバーを再描画します。

VODストリームに対して遅延広告解決を有効にすると、すべての広告の時間がタイムラインに配置されますが、広告の時間の多くはまだ解決されません。 アプリケーションは、`TimelineMarker::getDuration()`をチェックして、これらのマーカーを描画するかどうかを決定できます。 値が0より大きい場合は、広告の時間内の広告が解決されています。

TVSDKは、広告の時間が解決されたときにも、また、プレイヤーがPREPAREDステータスにトランジションしたときにも、このイベントをディスパッチします。

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
