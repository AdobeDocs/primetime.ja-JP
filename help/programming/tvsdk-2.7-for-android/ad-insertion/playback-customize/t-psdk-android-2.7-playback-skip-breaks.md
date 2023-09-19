---
description: デフォルトでは、 TVSDK は、ユーザーが広告の時間をシークオーバーする際に、広告の時間を強制的に再生します。 動作をカスタマイズして、前のブレーク完了からの経過時間が一定の分数以内の場合に、広告ブレークをスキップすることができます。
title: 一定期間広告の時間をスキップ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 一定期間広告の時間をスキップ {#skip-ad-breaks-for-a-period-of-time}

デフォルトでは、 TVSDK は、ユーザーが広告の時間をシークオーバーする際に、広告の時間を強制的に再生します。 動作をカスタマイズして、前のブレーク完了からの経過時間が一定の分数以内の場合に、広告ブレークをスキップすることができます。

>[!IMPORTANT]
>
>広告を許可するために内部シークを完了する必要がある場合、再生中に若干の一時停止が発生する可能性があります。

デフォルトの TVSDK 広告ブレーク動作を上書きするには、デフォルトの広告ポリシーセレクターを拡張します。 次の 4 つの広告ブレークポリシーを使用できます。

* 再生
* スキップ

  >[!NOTE]
  >
  >広告がライブポイントに存在する場合、ライブストリームでは、スキップ広告ブレークポリシーが期待どおりに機能しない可能性があります。 例えば、プリロールの場合、SKIP は広告ブレークの終わりまでのシークを引き起こします（ライブポイントより大きい可能性があります）。 この場合、 TVSDK は広告の途中をシークする可能性があります。

* REMOVE_AFTER
* 削除

  >[!NOTE]
  >
  >The `REMOVE` 広告ブレークポリシーは廃止予定です。 Adobeでは、 `SKIP` 代わりに広告ブレークポリシー `REMOVE`.

次に、カスタマイズされた広告ポリシーセレクターの例では、ユーザーが広告の時間を視聴した後、5 分（ウォール時刻）以内に広告をスキップします。

1. ユーザーが広告の時間の視聴を終了したら、現在のシステム時間を保存します。

   ```java
   @Override 
   public void onAdBreakComplete(AdBreak adBreak) { 
       ... 
       if (isShouldPlayUpcomingAdBreakRuleEnabled()) { 
           CustomAdPolicySelector.setLastAdBreakPlayedTime(System.currentTimeMillis()); 
           ... 
       } 
   }
   ```

1. 拡張 `AdPolicySelector`.

   ```java
   package com.adobe.mediacore.sample.advertising; 
   
   import com.adobe.mediacore.MediaPlayerItem; 
   import com.adobe.mediacore.MediaPlayerItemConfig; 
   import com.adobe.mediacore.timeline.advertising.policy.*; 
   import com.adobe.mediacore.timeline.advertising.AdBreakTimelineItem; 
   import com.adobe.mediacore.metadata.AdvertisingMetadata; 
   
   import java.util.ArrayList; 
   import java.util.List; 
   
   public class CustomAdPolicySelector implements AdPolicySelector { 
   
       private static final long MIN_BREAK_INTERVAL = 300000; // 5 minutes for next ad break to be played 
       private MediaPlayerItem _mediaPlayerItem; 
       private static long _lastAdBreakPlayedTime; 
       private AdBreakWatchedPolicy watchedPolicy = AdBreakWatchedPolicy.WATCHED_ON_BEGIN; 
   
       public CustomAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
           _mediaPlayerItem = mediaPlayerItem; 
           _lastAdBreakPlayedTime = 0; 
   
           if (mediaPlayerItem != null) { 
               watchedPolicy = extractWatchedPolicy(mediaPlayerItem.getConfig()); 
           } 
       } 
   
       @Override 
       public AdBreakPolicy selectPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
           if (shouldPlayAdBreaks() && adPolicyInfo.getAdBreakTimelineItems() != null) { 
   
               AdBreakTimelineItem item = adPolicyInfo.getAdBreakTimelineItems().get(0); 
   
               // This condition will remove the pre-roll ad from live stream after watching 
               if (item.getTime() == 0 && _mediaPlayerItem.isLive()) { 
                   return AdBreakPolicy.REMOVE_AFTER_PLAY; 
               } 
               if (item.getTime() == 0) { 
                   return AdBreakPolicy.PLAY; 
               } 
   
               // This condition will remove every ad break that has been watched once.  
               // Comment this section if you want to play watched ad breaks again. 
               if (item.isWatched()) { 
                   return AdBreakPolicy.SKIP; 
               } 
   
               return AdBreakPolicy.REMOVE_AFTER_PLAY; 
           } 
   
           return AdBreakPolicy.SKIP; 
       } 
   
       @Override 
       public List<AdBreakTimelineItem> selectAdBreaksToPlay(AdPolicyInfo adPolicyInfo) { 
   
           if (shouldPlayAdBreaks()) { 
   
               List<AdBreakTimelineItem> timelineItems = adPolicyInfo.getAdBreakTimelineItems(); 
               AdBreakTimelineItem item; 
               List<AdBreakTimelineItem> selectedItems = new ArrayList<AdBreakTimelineItem>(); 
   
               if (timelineItems != null && timelineItems.size() > 0) { 
   
                   // Seek Forward Condition 
                   if (adPolicyInfo.getCurrentTime() <= adPolicyInfo.getSeekToTime()) { 
                       item = timelineItems.get(0); 
   
                       // Resume logic - This will be helpful in resuming the content  
                       // from last saved playback session, and just play the pre-roll ad 
                       if(adPolicyInfo.getCurrentTime() == 0) { 
                           if(item.getTime() == 0 && !item.isWatched()) { 
                               // comment this line if you just need to seek to the user's  
                               // last known position without playing pre-roll ad. ZD#820 
                               selectedItems.add(item); 
                               return selectedItems; 
                           } 
                           else{ 
                               return null; 
                           } 
                       } else { 
                           item = timelineItems.get(timelineItems.size()-1); 
                           if (!item.isWatched()) { 
                               selectedItems.add(item); 
                               return selectedItems; 
                           } 
                       } 
   
                       // Seek backward condition 
                   } else if (adPolicyInfo.getCurrentTime() > adPolicyInfo.getSeekToTime()) { 
                       item = timelineItems.get(0); 
   
                       if(!item.isWatched()) { 
                           selectedItems.add(item); 
                           return selectedItems; 
                       } else { 
                           return null; 
                       } 
                   } 
               } 
           } 
           return null; 
       } 
   
       @Override 
       public AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo) { 
           // Simple Ad Policy selector 
           // if the first ad in the break was watched,  
           // skip to the next add after the seek position 
           // otherwise, play the ads in the break from the beginning 
   
           List<AdBreakTimelineItem> timelineItems = adPolicyInfo.getAdBreakTimelineItems(); 
           if (timelineItems != null && timelineItems.size() > 0) { 
               if (timelineItems.get(0).isWatched()) { 
                   return AdPolicy.SKIP_TO_NEXT_AD_IN_AD_BREAK; 
               } 
           } 
   
           // Resume play from the next ad in the break 
           return AdPolicy.PLAY_FROM_AD_BREAK_BEGIN; 
   
       } 
   
       @Override 
       public AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
           return watchedPolicy; 
       } 
   
       public static void setLastAdBreakPlayedTime(long lastAdBreakPlayedTime) { 
           _lastAdBreakPlayedTime = lastAdBreakPlayedTime; 
       } 
   
       private boolean shouldPlayAdBreaks() { 
           long currentTime = System.currentTimeMillis(); 
   
           if (_lastAdBreakPlayedTime <= 0) { 
               return true; 
           } 
   
           if (_lastAdBreakPlayedTime > 0 &&  
             (currentTime - _lastAdBreakPlayedTime) > MIN_BREAK_INTERVAL) { 
               return true; 
           } 
   
           // return false for not playing Ad if this  
           // Ad occurs with 5 minutes of last Ad playback 
           return false; 
       } 
   
       private AdBreakWatchedPolicy extractWatchedPolicy(MediaPlayerItemConfig config) { 
           if (config != null) { 
               AdvertisingMetadata metadata = config.getAdvertisingMetadata(); 
               if (metadata != null) { 
                   return metadata.getAdBreakWatchedPolicy(); 
               } 
           } 
           return AdBreakWatchedPolicy.WATCHED_ON_BEGIN; 
       } 
   } 
   ```
