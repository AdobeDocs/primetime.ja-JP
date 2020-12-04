---
description: テレビのようなエクスペリエンスで、広告の途中やライブストリームに参加できるようにすることができます。
seo-description: テレビのようなエクスペリエンスで、広告の途中やライブストリームに参加できるようにすることができます。
seo-title: 広告の時間の部分挿入
title: 広告の時間の部分挿入
uuid: 296a9b6a-9e9f-4ca7-ab8a-c8cbc98fb9af
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# 部分的な広告ブレークの挿入{#partial-ad-break-insertion}

テレビのようなエクスペリエンスで、広告の途中やライブストリームに参加できるようにすることができます。

部分的な広告の時間機能を使用すると、クライアントがミッドロール内のライブストリームを開始した場合に、そのミッドロール内で開始する、テレビのようなエクスペリエンスを模倣できます。 テレビチャネルに切り替えるのと同じで、CMはシームレスに走ります。

例えば、ユーザーが90秒の広告の時間（3つの30秒の広告）の途中で加入し、10秒で2番目の広告に入った場合（つまり、広告の時間が始まる40秒の時点）、次のようになります。

* 2番目の広告は、残りの時間（20秒）に再生され、次に3番目の広告が再生されます。
* 部分的に再生された広告（2番目の広告）の広告トラッカーは起動されません。 3番目の広告のトラッカーのみが起動されます。

この動作は、デフォルトでは有効になっていません。 アプリでこの機能を有効にするには、次の手順を実行します。

1. AdvertisingMetadataクラスのメソッドsetEnableLivePrerollを使用して、ライブプリロールを無効にします。

   ```
   advertisingMetadata.setEnableLivePreroll(String.valueOf(false))
   ```

1. 部分的な広告ブレークの挿入の環境設定をオンにします。 この機能をオンにするには、MediaPlayerインターフェイスの新しいメソッドsetPartialAdBreakPrefを使用します。 この基本設定の現在の状態を調べるには、getPartialAdBreakPrefメソッドを使用します。

   ```
   MediaPlayer mediaPlayer = DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
   
          mediaPlayer.setPartialAdBreakPref(true); 
   ```

1. この機能を使用するには、カスタム広告ポリシーセレクターを実装して動作をカスタマイズする必要があります。 AdvertisingFactoryクラスのカスタム実装をまだ持っていない場合は、新しいAdvertisingFactory実装を追加します。 createAdPolicySelectorメソッドを上書きします。 このメソッドは、AdPolicySelectorの実装の新しいインスタンスを返します。

   参考用に、実装の例を以下に示します。 次の実装例は、com.adobe.mediacoreパッケージで使用できます。 ただし、参照しやすいように簡単になっており、そのまま使用することはお勧めしません。

   1. 広告ポリシーセレクターの例

      ```
       package com.adobe.mediacore;
      
      import com.adobe.mediacore.logging.Log; 
      import com.adobe.mediacore.logging.Logger; 
      import com.adobe.mediacore.metadata.*; 
      import com.adobe.mediacore.timeline.advertising.*; 
      
      import java.util.ArrayList; 
      import java.util.List; 
      
      public class PartialAdBreakAdPolicySelector implements AdPolicySelector { 
          private static final String LOG_TAG = "[PSDK]::" + DefaultAdPolicySelector.class.getSimpleName(); 
          private final Logger _logger = Log.getLogger(LOG_TAG); 
      
          private final MediaPlayerItem _mediaPlayerItem; 
          private final AdBreakAsWatched _adBreakAsWatchedPolicy; 
      
          public PartialAdBreakAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
              _mediaPlayerItem = mediaPlayerItem; 
              _adBreakAsWatchedPolicy = extractAdBreakAsWatchedPolicy(_mediaPlayerItem); 
          } 
      
          @Override 
          public AdBreakPolicy selectPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectPolicyForAdBreak", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              if (adPolicyInfo.getAdBreakPlacements().size() > 0) { 
                  AdBreakPlacement adBreakTimelineItem = adPolicyInfo.getAdBreakPlacements().get(0); 
                  if (adPolicyInfo.getMode() == AdPolicyMode.SEEK && adBreakTimelineItem.getAdBreak().isWatched()) { 
                      return AdBreakPolicy.SKIP; 
                  } 
              } 
      
              AdSignalingMode adSignalingMode = AdSignalingMode.DEFAULT; 
              if (_mediaPlayerItem != null) { 
                  MetadataNode metadata = (MetadataNode) _mediaPlayerItem.getResource().getMetadata(); 
                  if (metadata != null) { 
                      AdvertisingMetadata advertisingMetadata = (AdvertisingMetadata) metadata.getNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue()); 
                      if (advertisingMetadata != null) { 
                          adSignalingMode = advertisingMetadata.getSignalingMode(); 
                      } 
                  } 
              } 
      
              // can't remove main content due to a ave bug, need to check if stream is live or ad signaling mode is manifest cue 
              if (_mediaPlayerItem.isLive() || adSignalingMode == AdSignalingMode.MANIFEST_CUES) { 
                  return AdBreakPolicy.PLAY; 
              } 
      
              return AdBreakPolicy.REMOVE_AFTER_PLAY; 
          } 
      
          @Override 
          public List<AdBreakPlacement> selectAdBreaksToPlay(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectAdBreaksToPlay", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              List<AdBreakPlacement> adBreakPlacements = adPolicyInfo.getAdBreakPlacements(); 
              if (adBreakPlacements != null) { 
                  int size = adBreakPlacements.size(); 
                  List<AdBreakPlacement> adBreaks = new ArrayList<AdBreakPlacement>(); 
                  if (size > 0 && adPolicyInfo.getCurrentTime() <= adPolicyInfo.getSeekToTime()) { 
                      AdBreakPlacement adBreak = adBreakPlacements.get(size - 1); 
                      if (!adBreak.getAdBreak().isWatched()) { 
                          adBreaks.add(adBreak); 
                          return adBreaks; 
                      } 
                  } 
              } 
      
              return null; 
          } 
      
          @Override 
          public AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectPolicyForSeekIntoAd", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              // If you really want to allow seek during ads (you likely do not). 
              return AdPolicy.PLAY; 
          } 
      
          @Override 
          public AdBreakAsWatched selectWatchedPolicyForAdBreak(AdPolicyInfo adPolicyInfo) { 
              _logger.i(LOG_TAG + "#selectWatchedPolicyForAdBreak", "currentTime=" + adPolicyInfo.getCurrentTime() + " seekToTime=" 
                      + adPolicyInfo.getSeekToTime() + " rate=" + adPolicyInfo.getRate() + " adPolicyMode=" + adPolicyInfo.getMode()); 
      
              return _adBreakAsWatchedPolicy; 
          } 
      
          /** 
           * Extract the ad break watched policy for the specified media player item. 
           * 
           * @param item Associated media player item. 
           * @return a valid ad break watched policy. 
           */ 
          private AdBreakAsWatched extractAdBreakAsWatchedPolicy(MediaPlayerItem item) { 
              AdBreakAsWatched adBreakWatchedPolicy = AdBreakAsWatched.AD_BREAK_AS_WATCHED_ON_BEGIN; 
      
              if (item != null) { 
                  MetadataNode metadata = (MetadataNode) item.getResource().getMetadata(); 
                  if (metadata != null) { 
                      AdvertisingMetadata advertisingMetadata = (AdvertisingMetadata) metadata.getNode(DefaultMetadataKeys.ADVERTISING_METADATA.getValue()); 
                      if (advertisingMetadata != null) { 
                          adBreakWatchedPolicy = advertisingMetadata.getAdBreakAsWatched(); 
                      } 
                  } 
              } 
      
              return adBreakWatchedPolicy; 
          } 
      } 
      ```

   1. 広告ファクトリのサンプル

      ```
      private AdvertisingFactory createPartialAdBreakFactory() { 
      return new AdvertisingFactory() { 
      @Override 
                   public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
                      return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
                   } 
      
      // Rest of the interface methods can be overridden as per your  
      // customization needs 
      // As shown next 
      @Override 
      public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
         return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
        } 
      // . . . 
      
       } 
      } 
      ```

   1. アドビのAdvertisingFactoryをメディアプレイヤーに登録します

      ```
      AdvertisingFactory advertisingFactory = createPartialAdBreakFactory();  
      
      if (advertisingFactory != null) { 
                  mediaPlayer.registerAdClientFactory(advertisingFactory); 
      } 
      ```

   1. createAdPolicySelectorメソッドの上書き

      ```
      @Override 
      public AdPolicySelector  
      createAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
         return new PartialAdBreakAdPolicySelector(mediaPlayerItem); 
      } 
      ```

