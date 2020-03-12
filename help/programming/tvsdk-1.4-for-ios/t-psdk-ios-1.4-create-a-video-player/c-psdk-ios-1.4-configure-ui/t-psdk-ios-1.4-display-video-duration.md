---
description: 現在アクティブなコンテンツの長さを表示できます。
seo-description: 現在アクティブなコンテンツの長さを表示できます。
seo-title: ビデオの長さの表示
title: ビデオの長さの表示
uuid: 02042070-9c55-4cbb-9dc1-49987451eb8f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ビデオの長さの表示 {#display-the-duration-of-the-video}

現在アクティブなコンテンツの長さを表示できます。

次のサンプルコードを使用して、ビデオの長さの表示を実装します。

    &#39;PTMediaPlayer&#39;プロパティ[seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)には、現在のシーク可能なウィンドウ範囲が含まれます。
    
    * VODの場合、この範囲は広告を含むVODコンテンツ範囲全体です。
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
