---
description: ライブストリーム広告の挿入の場合、ブレーク内のすべての広告が最後まで再生される前に、広告ブレークから終了する必要が生じる場合があります。
title: 早期広告ブレークリターンの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 早期広告ブレークリターンの実装 {#implement-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、ブレーク内のすべての広告が最後まで再生される前に、広告ブレークから終了する必要が生じる場合があります。

例えば、特定のスポーツイベントでの広告ブレークの期間が、ブレークの開始前にわからない場合があります。 TVSDK はデフォルトのデュレーションを提供しますが、ブレークが終了する前にゲームが再開された場合は、広告ブレークを終了する必要があります。 もう 1 つの例は、ライブストリームの広告ブレーク中の緊急シグナルです。

1. スプライスアウト/イン広告マーカー ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`、および `#EXT-X-CUE`) をクリックします。

   広告マーカーをスプライスする方法について詳しくは、 [オポチュニティジェネレーターとコンテンツリゾルバー](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md).
1. カスタムを使用 `ContentFactory`.
1. In `retrieveGenerators()`を使用する場合は、 `SpliceInPlacementOpportunityGenerator`.

   例：

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   カスタムの使用に関する詳細 `ContentFactory`詳しくは、手順 1 を参照してください。 [カスタムオポチュニティディテクターの実装](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md) .

1. 同じカスタムで `ContentFactory`，実装 `retrieveResolvers` およびを含む `AuditudeResolver` および `SpliceInCustomResolver`.

   例：

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```
