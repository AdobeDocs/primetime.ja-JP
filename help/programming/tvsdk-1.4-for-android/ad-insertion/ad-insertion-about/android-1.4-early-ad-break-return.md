---
description: ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。
title: 早期の広告ブレークリターンの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 2%

---


# 早期広告ブレークリターンの実装{#implement-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。

例えば、特定のスポーツイベントでの広告の時間の継続時間が、その時間の開始前にわからない場合があります。 TVSDKはデフォルトの継続時間を提供しますが、ゲームが終了する前に再開される場合は、広告の時間を終了する必要があります。 もう1つの例は、ライブストリーム内の広告の時間中の緊急信号です。

1. スプライスの広告マーカー(`#EXT-X-CUE-OUT`、`#EXT-X-CUE-IN`、`#EXT-X-CUE`)を登録します。

   広告マーカーを繋ぎ合わせる方法の詳細については、[オポチュニティジェネレーターとコンテンツリゾルバー](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-content-resolver-about.md)を参照してください。
1. カスタム`ContentFactory`を使用します。
1. `retrieveGenerators()`では、`SpliceInPlacementOpportunityGenerator`を使用します。

   例：

   ```java
   public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { 
       List<OpportunityGenerator> generators = new ArrayList<OpportunityGenerator>(); 
       generators.add(SpliceInPlacementOpportunityDetector(item)); 
       return generators; 
   }
   ```

   カスタム`ContentFactory`の使用について詳しくは、[カスタムオポチュニティディテクターの実装](../../../tvsdk-1.4-for-android/content-resolver/android-1.4-opp-detector-impl.md)の手順1を参照してください。

1. 同じカスタム`ContentFactory`で、`retrieveResolvers`を実装し、`AuditudeResolver`と`SpliceInCustomResolver`を含めます。

   例：

   ```java
   List<ContentResolver> contentResolvers = new ArrayList<ContentResolver>(); 
   contentResolvers.add(new AuditudeResolver(getActivity().getApplicationContext())); 
   contentResolvers.add(new SpliceInCustomResolver()); 
   return contentResolvers;
   ```

