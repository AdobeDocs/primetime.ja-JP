---
description: 遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（デフォルトでは、遅延広告解決が有効になっています）。
keywords: 遅延；広告解決；広告読み込み；遅延読み込み
title: 遅延広告解決の有効化
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# 遅延広告解決を有効にする{#enable-lazy-ad-resolving}

遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（デフォルトでは、遅延広告解決が有効になっています）。

[AdvertisingMetadata.setDelayLoading](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html#setDelayAdLoading-boolean-)を`true`または`false`と共に呼び出すことで、遅延広告解決を有効または無効にできます。

1. 広告解決のタイミングとタイムライン上の広告の配置を制御するには、`AdvertisingMetadata`のブール値`hasDelayAdLoading`メソッドと`setDelayAdLoading`メソッドを使用します。

   * `hasDelayAdLoading`がfalseを返した場合、TVSDKは、すべての広告が解決され、配置されてから、PREPARED状態に移行します。
   * `hasDelayAdLoading`がtrueを返した場合、TVSDKは、最初の広告とトランジションのみをPREPARED状態に解決します。 残りの広告は再生中に解決され、配置されます。
   * `hasPreroll`または`hasLivePreroll`がfalseを返すと、TVSDKは、プリロール広告がないと見なし、コンテンツの直ちに再生を開始します。 デフォルトはtrueです。

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

1. 広告をスクラブバーのキューとして正確に反映させるには、`TimelineEvent`イベントをリッスンし、このイベントを受け取るたびにスクラブバーを再描画します。

   VODストリームに対して遅延広告解決を有効にすると、プレイヤーがPREPARED状態になったときにすべての広告がタイムラインに配置されないので、プレイヤーはスクラブバーを明示的に再描画する必要があります。

   TVSDKは、このイベントのディスパッチを最適化して、スクラブバーを再描画する必要がある回数を最小限に抑えます。したがって、タイムラインイベントの数は、タイムライン上に配置される広告の時間の数とは関係ありません。 例えば、5つの広告の時間がある場合、厳密には5つのイベントを受け取らないことがあります。

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

>遅延広告解決機能が有効または無効になっているかどうかを確認するには、`AdvertisingMetadata.hasDelayAdLoading`を呼び出します。 戻り値`true`は、遅延広告解決が有効であることを意味します。`false`は、機能が無効になっていることを意味します。

