---
description: 既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決は無効になっています）。
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: 既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決は無効になっています）。
seo-title: 遅延広告解決の有効化
title: 遅延広告解決の有効化
uuid: 91884eea-a622-4f5d-b6a8-36bb0050ba1d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 遅延広告解決の有効化 {#enable-lazy-ad-resolving}

既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決は無効になっています）。

AdvertisingMetadata.setDelayLoadingをtrueまたはfalseで呼び出すことで、遅延広告解 [決を有効または無効にできます](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) 。

* 広告の解決のタイミ *ングとタイムライン上の広告の配置を制御するには、AdvertisingMetadataのBoolean* hasDelayAdLoading ** メソッドとsetDelayAdLoadingメソッドを使用します。

   * hasDelayAdLoading *がfalseを返す場合* 、TVSDKは、すべての広告が解決され、配置されてからPREPARED状態に移行します。
   * hasDelayAdLoading *がtrueを返す場合* 、TVSDKは初期広告のみを解決し、PREPARED状態に移行します。

      * 残りの広告は、再生中に解決され、配置されます。
   * *hasPreroll *またはhasLivePreroll ** falseが返された場合、TVSDKはプリロール広告がないと見なし、コンテンツの再生を直ちに開始します。 これらはデフォルトでtrueに設定されています。


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

広告をスクラブバーのキューとして正確に反映するには、イベントをリッスンし、こ `TimelineEvent`のイベントを受け取るたびにスクラブバーを再描画します。

VODストリームに対して遅延広告解決を有効にすると、すべての広告の時間がタイムラインに配置されますが、多くの広告の時間はまだ解決されません。 これらのマーカーを描画するかどうかは、を確認することで判断できま `TimelineMarker::getDuration()`す。 値が0より大きい場合、広告の時間内の広告は解決されました。

TVSDKは、広告の時間が解決されたときと、プレイヤーがPREPAREDステータスに移行したときに、このイベントをディスパッチします。

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
