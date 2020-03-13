---
description: 既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決が有効になっています）。
keywords: Lazy;Ad resolving;Ad loading;delayLoading
seo-description: 既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決が有効になっています）。
seo-title: 遅延広告解決の有効化
title: 遅延広告解決の有効化
uuid: a084ee0b-53af-4600-91f6-d30ccc89699d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 遅延広告解決の有効化 {#enable-lazy-ad-resolving}

既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決が有効になっています）。

またはを使用してAdvertisingMetadata.setDelayLoadingを呼び出すことで、遅延広告解 [決を有効または無効にで](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) きま `true``false`す。

1. のブール値とメソッ `hasDelayAdLoading` ドを使 `setDelayAdLoading` 用して、 `AdvertisingMetadata` 広告の解決のタイミングと、広告のタイムライン上での配置を制御します。

   * falseを返 `hasDelayAdLoading` した場合、TVSDKは、すべての広告が解決され、配置されてから、PREPARED状態に移行します。
   * trueを返 `hasDelayAdLoading` すと、TVSDKは最初の広告のみを解決し、PREPARED状態に移行します。 残りの広告は、再生中に解決され、配置されます。
   * TVSDKは、 `hasPreroll` ま `hasLivePreroll` たはfalseを返す場合、プリロール広告がないと見なし、コンテンツの再生を直ちに開始します。 デフォルトはtrueです。

      遅延広告解決に関連するAPI:

      ```
      Class: 
         com.adobe.mediacore.metadata.AdvertisingMetadata 
      
      Methods: 
      […] 
          public final boolean hasDelayAdLoading() // Check if Lazy Ad Resolving enabled 
          public final void setDelayAdLoading()    // Enable or disable Lazy Ad Resolving 
          public final boolean hasPreroll()        // Check for existence of pre-roll ads 
          public final void setPreroll()           // Set pre-roll true or false 
          public final boolean hasLivePreroll()    // Check for live pre-roll ads 
          public final void setLivePreroll()       // Set live pre-roll true or false 
      […]
      ```

1. 広告をスクラブバーのキューとして正確に反映するには、イベントをリッスンし、このイベ `TimelineEvent` ントを受け取るたびにスクラブバーを再描画します。

   VODストリームに対して遅延広告解決を有効にすると、プレイヤーがPREPARED状態になったときに、すべての広告がタイムラインに配置されないので、プレイヤーはスクラブバーを明示的に再描画する必要があります。

   TVSDKは、このイベントのディスパッチを最適化して、スクラブバーを再描画する必要のある回数を最小限に抑えます。したがって、タイムラインイベントの数は、タイムライン上に配置される広告の時間の数とは関係ありません。 例えば、5つの広告の時間がある場合、正確に5つのイベントを受け取らない可能性があります。

   ```java
   mediaPlayer.addEventListener 
       (MediaPlayerEvent.TIMELINE_UPDATED, timelineUpdatedEventListener); 
   /** 
    * ... 
    */ 
   public void onTimelineUpdated(TimelineEvent event) { 
   
       for (PlaybackManagerEventListener listener : eventListeners) { 
           listener.onUpdate(getLocalSeekRange(), event.getTimeline()); 
       } 
   } 
   ```

>遅延広告解決機能が有効か無効かを確認するには、を呼び出しま `AdvertisingMetadata.hasDelayAdLoading`す。 の戻り値は、遅延広告 `true` 解決が有効であることを意味します。機能が `false` 無効になっていることを意味します。

