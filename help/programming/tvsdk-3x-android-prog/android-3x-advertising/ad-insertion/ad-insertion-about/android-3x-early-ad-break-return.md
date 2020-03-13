---
description: ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。
seo-description: ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。
seo-title: 早期の広告ブレークリターンの実装
title: 早期の広告ブレークリターンの実装
uuid: 0e77414e-86f5-4979-9caa-eaf2f39144a2
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# 早期の広告ブレークリターンの実装 {#implement-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。

例えば、特定のスポーツイベントでの広告の時間の長さが、時間が始まる前にわからない場合があります。 TVSDKはデフォルトの時間を提供しますが、時間が終了する前にゲームが再開した場合は、広告の時間を終了する必要があります。 もう1つの例は、ライブストリームの広告の時間中の緊急信号です。

1. マーカー内の `#EXT-X-CUE-OUT`スプ `#EXT-X-CUE-IN`ライスア `#EXT-X-CUE`ウト/スプライスである、、、およびをサブスクライブします。
広告マーカーをスプライスアウト/インする方法について詳しくは、「オポチュニティジェネレーターとコン [テンツリゾルバー」を参照してくださ](../../ad-insertion/content-resolver/android-3x-content-resolver.md)い。
1. カスタムを使用しま `ContentFactory`す。
1. で、 `retrieveGenerators`を使用します `SpliceInPlacementOpportunityGenerator`。

   例：

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   カスタムオポチュニティジェネレーターの実装 `ContentFactory`の手順1を参照し [てください](../../ad-insertion/content-resolver/android-3x-opp-detector-impl-android.md)。

1. 同じカスタムで、とを `ContentFactory`実装し、 `retrieveResolvers` を含め `AuditudeResolver` ます `SpliceInCustomResolver`。

   例：

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
