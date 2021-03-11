---
description: 現在アクティブなコンテンツの長さを表示できます。
title: ビデオの長さの表示
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# ビデオの長さの表示{#display-the-duration-of-the-video}

現在アクティブなコンテンツの長さを表示できます。

以下のサンプルコードを使用して、ビデオの長さの表示を実装します。

    &#39;PTMediaPlayer&#39;プロパティ[seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)は、現在のシーク可能な時間範囲を含みます。
    
    * VODの場合、この範囲は広告を含むVODコンテンツ全体です。
    *ライブ/リニアの場合、この範囲はシーク可能な時間を表します。
    
    APIについて詳しくは、[TVSDK 1.4 for iOS API Reference](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/index.html)を参照してください。

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
