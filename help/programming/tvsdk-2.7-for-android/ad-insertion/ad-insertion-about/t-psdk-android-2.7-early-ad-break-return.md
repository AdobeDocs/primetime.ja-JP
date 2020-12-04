---
description: ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。
seo-description: ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。
seo-title: 早期の広告ブレークリターンの実装
title: 早期の広告ブレークリターンの実装
uuid: c67f2158-5df4-458c-a27a-6329c5d26638
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 1%

---


# 早期広告ブレークリターンの実装{#implement-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。

例えば、特定のスポーツイベントでの広告の時間の継続時間が、その時間の開始前にわからない場合があります。 TVSDKはデフォルトの継続時間を提供しますが、ゲームが終了する前に再開される場合は、広告の時間を終了する必要があります。 もう1つの例は、ライブストリーム内の広告の時間中の緊急信号です。

1. `#EXT-X-CUE-OUT`、`#EXT-X-CUE-IN`、および`#EXT-X-CUE`に登録します。これはマーカー内のスプライス出力/スプライスです。

   広告マーカーを繋ぎ合わせる方法の詳細については、[オポチュニティジェネレーターとコンテンツリゾルバー](../../ad-insertion/content-resolver/c-psdk-android-2.7-content-resolver-about.md)を参照してください。

1. カスタム`ContentFactory`を使用します。
1. `retrieveGenerators`では、`SpliceInPlacementOpportunityGenerator`を使用します。

   例：

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   カスタム`ContentFactory`の使用について詳しくは、[カスタムオポチュニティジェネレーターの実装](../../ad-insertion/content-resolver/t-psdk-android-2.7-opp-detector-impl-android.md)の手順1を参照してください。

1. 同じカスタム`ContentFactory`で、`retrieveResolvers`を実装し、`AuditudeResolver`と`SpliceInCustomResolver`を含めます。

   例：

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

