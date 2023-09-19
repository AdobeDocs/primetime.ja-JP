---
description: デフォルトでは、 TVSDK は、ユーザーが広告の時間をシークオーバーする際に、広告の時間を強制的に再生します。 動作をカスタマイズして、前のブレーク完了からの経過時間が一定の分数以内の場合に、広告ブレークをスキップすることができます。
title: 一定期間広告の時間をスキップ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# 一定期間広告の時間をスキップ{#skip-ad-breaks-for-a-period-of-time}

デフォルトでは、 TVSDK は、ユーザーが広告の時間をシークオーバーする際に、広告の時間を強制的に再生します。 動作をカスタマイズして、前のブレーク完了からの経過時間が一定の分数以内の場合に、広告ブレークをスキップすることができます。

>[!IMPORTANT]
>
>広告をスキップする内部シークがある場合、再生で少し一時停止が発生している可能性があります。

次に、カスタマイズされた広告ポリシーセレクターの例では、ユーザーが広告の時間を視聴した後、5 分（ウォール時刻）以内に広告をスキップします。

1. デフォルトの広告ポリシーセレクターを拡張して、デフォルトの動作を上書きします。

   ```
   /** 
    * Custom ad policy selector. 
    */ 
   public class CustomAdPolicySelector extends DefaultAdPolicySelector { 
   
       /** 
        * Default constructor. 
        * 
        * @param item Associated media player item. 
        */ 
       public function CustomAdPolicySelector(item:MediaPlayerItem) { 
           super(item); 
   
           item.player.addEventListener(AdBreakPlaybackEvent.AD_BREAK_COMPLETED,  
                                        onAdBreakCompleted); 
       } 
   
       override public function selectPolicyForAdBreak(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForAdBreak(adPolicyInfo); 
           } 
   
           return AdBreakPolicy.SKIP; 
       } 
   
       override public function selectAdBreaksToPlay(adPolicyInfo:AdPolicyInfo):Vector.<AdBreakTimelineItem> { 
           if (shouldPlayAds()) { 
               return super.selectAdBreaksToPlay(adPolicyInfo); 
           } 
   
           return new Vector.<AdBreakTimelineItem>(); 
       } 
   
       override public function selectPolicyForSeekIntoAd(adPolicyInfo:AdPolicyInfo):String { 
           if (shouldPlayAds()) { 
               return super.selectPolicyForSeekIntoAd(adPolicyInfo); 
           } 
   
           return AdPolicy.SKIP_TO_NEXT_AD_IN_AD_BREAK; 
       } 
   
       private function onAdBreakCompleted(event:AdBreakPlaybackEvent):void { 
           _lastAdBreakPlayedTime = new Date().valueOf(); 
       } 
   
       private function shouldPlayAds():Boolean { 
           var currentTime:Number = new Date().valueOf(); 
           return isNaN(_lastAdBreakPlayedTime) 
                   ||  (currentTime - _lastAdBreakPlayedTime > _minimumInterval); 
       } 
   
       private var _lastAdBreakPlayedTime:Number = NaN; 
       private var _minimumInterval:Number = 300000; // 5 minutes in milliseconds 
   }
   ```

1. カスタムセレクターを使用する新しい広告ファクトリを作成します。

   ```
   public class CustomAdPolicyContentFactory extends DefaultContentFactory { 
   
       private var _adPolicySelector:CustomAdPolicySelector; 
   
       /** 
        * Default constructor. 
        */ 
       public function CustomAdPolicyContentFactory() { 
   
       } 
   
       /** 
       * @inheritDoc 
       */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
       if (!_adPolicySelector) { 
           _adPolicySelector = new CustomAdPolicySelector(item); 
       } 
   
       return _adPolicySelector; 
       } 
   }
   ```

1. 使用する新しい広告ファクトリクラスを MediaPlayer に登録します。

   ```
   var mediaResource:MediaResource =  
     MediaResource.createFromUrl("https://example.org/stream.m3u8", null); 
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     PSDKConfig.retrieveMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomAdPolicyContentFactory(); 
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```
