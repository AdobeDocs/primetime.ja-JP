---
description: ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。
seo-description: ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。
seo-title: 早期の広告ブレークリターンの実装
title: 早期の広告ブレークリターンの実装
uuid: 41b70ee1-290b-4732-899e-32b234ec1d9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 早期の広告ブレークリターンの実装 {#implement-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。

例えば、特定のスポーツイベントでの広告の時間の長さが、時間が始まる前にわからない場合があります。 TVSDKはデフォルトの時間を提供しますが、時間が終了する前にゲームが再開した場合は、広告の時間を終了する必要があります。 もう1つの例は、ライブストリームの広告の時間中の緊急信号です。

1. スプライスの広告マーカー(、、お `#EXT-X-CUE-OUT`よび `#EXT-X-CUE-IN`)を登録 `#EXT-X-CUE`します。

   広告マーカーをスプライスアウト/インする方法について詳しくは、「オポチュニティジェネレーターとコン [テンツリゾルバー」を参照してくださ](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md)い。
1. カスタムを使用しま `ContentFactory`す。
1. で、 `retrieveGenerators()`を使用します `SpliceInPlacementOpportunityGenerator`。

   例：

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   カスタムオポチュニティディテクターの使用につい `ContentFactory`て詳しくは、「カスタムオポチュニテ [ィディテクターの実装」の手順1を参照してくださ](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) い。

1. 同じカスタムで、とを `ContentFactory`実装し、 `retrieveResolvers` を含め `AuditudeResolver` ます `SpliceInCustomResolver`。

   例：

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

