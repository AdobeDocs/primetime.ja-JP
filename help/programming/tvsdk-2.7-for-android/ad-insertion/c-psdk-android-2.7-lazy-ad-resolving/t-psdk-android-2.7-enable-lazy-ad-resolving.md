---
description: 遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（遅延広告解決はデフォルトで有効になっています）。
keywords: 遅延；広告解決；広告の読み込み；delayLoading
title: 遅延広告解決を有効にする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 遅延広告解決を有効にする {#enable-lazy-ad-resolving}

遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（遅延広告解決はデフォルトで有効になっています）。

遅延広告解決は、 [AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-) 次を使用 `true` または `false`.

1. ブール値を使用 `hasDelayAdLoading` および `setDelayAdLoading` メソッド内 `AdvertisingMetadata` 広告の解決のタイミングとタイムラインでの広告の配置を制御するには：

   * 次の場合 `hasDelayAdLoading` false を返す場合、 TVSDK は、すべての広告が解決され、配置されてから、PREPARED 状態に移行します。
   * 次の場合 `hasDelayAdLoading` true を返します。 TVSDK は、最初の広告とトランジションのみを PREPARED 状態に解決します。 残りの広告は、再生中に解決され、配置されます。
   * 条件 `hasPreroll` または `hasLivePreroll` false を返す場合、 TVSDK はプリロール広告がないと仮定し、コンテンツの再生を直ちに開始します。 これらのデフォルト値は true です。

     遅延広告解決に関連する API:

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

1. 広告をスクラブバーのキューとして正確に反映させるには、 `TimelineEvent` イベントを受け取るたびに、スクラブバーを再描画してください。

   VOD ストリームに対して遅延広告解決を有効にした場合、プレーヤーが PREPARED 状態になったときにすべての広告がタイムラインに配置されるわけではないので、プレーヤーはスクラブバーを明示的に再描画する必要があります。

   TVSDK は、このイベントのディスパッチを最適化して、スクラブバーを再描画する必要がある回数を最小限に抑えます。したがって、タイムラインイベントの数は、タイムラインに配置する広告の時間の数とは関係ありません。 例えば、5 つの広告の時間がある場合、5 つのイベントを正確に受け取ることはありません。

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

>遅延広告解決機能が有効か無効かを確認するには、 `AdvertisingMetadata.hasDelayAdLoading`. の戻り値 `true` は、遅延広告解決が有効になっていることを意味し、 `false` は、機能が無効になっていることを意味します。
