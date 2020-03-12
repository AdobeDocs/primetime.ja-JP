---
description: デフォルトでは、TVSDKは、ユーザーが広告の時間をシークオーバーすると、広告の時間を強制的に再生します。 前の時間の完了からの経過時間が一定の分数以内である場合、広告の時間をスキップする動作をカスタマイズできます。
seo-description: デフォルトでは、TVSDKは、ユーザーが広告の時間をシークオーバーすると、広告の時間を強制的に再生します。 前の時間の完了からの経過時間が一定の分数以内である場合、広告の時間をスキップする動作をカスタマイズできます。
seo-title: 広告の時間を一定期間スキップ
title: 広告の時間を一定期間スキップ
uuid: 1a18d5fd-c957-481b-83ae-2129590c1678
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 広告の時間を一定期間スキップ{#skip-ad-breaks-for-a-period-of-time}

デフォルトでは、TVSDKは、ユーザーが広告の時間をシークオーバーすると、広告の時間を強制的に再生します。 前の時間の完了からの経過時間が一定の分数以内である場合、広告の時間をスキップする動作をカスタマイズできます。

>[!IMPORTANT]
>
>内部シークがあって広告をスキップする場合、再生が少し停止する場合があります。

次の例では、カスタマイズされた広告ポリシーセレクターを使用して、ユーザーが広告の時間を視聴した後、次の5分（時間枠）で広告をスキップします。

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

1. MediaPlayerで使用する新しい広告ファクトリクラスを登録します。

   ```
   var mediaResource:MediaResource =  
     MediaResource.createFromUrl("https://example.org/stream.m3u8", null); 
   var mediaPlayerItemConfig:MediaPlayerItemConfig =  
     PSDKConfig.retrieveMediaPlayerItemConfig(); 
   mediaPlayerItemConfig.advertisingFactory = new CustomAdPolicyContentFactory(); 
   player.replaceCurrentResource(mediaResource, mediaPlayerItemConfig);
   ```

