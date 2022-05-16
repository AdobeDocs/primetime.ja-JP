---
description: 現在アクティブなコンテンツの期間を表示できます。
title: ビデオのデュレーションを表示
exl-id: a41cb291-9355-44cf-80bb-9c3cf6628b81
source-git-commit: 85818281390b68522da2663496be025acf8f8675
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# ビデオのデュレーションを表示 {#display-the-duration-of-the-video}

現在アクティブなコンテンツの期間を表示できます。

以下のサンプルコードを使用して、ビデオの長さの表示を実装します。

この `PTMediaPlayer` プロパティ [seekableRange](https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html#//api/name/seekableRange)は、現在のシーク可能な範囲を含みます。

* VOD の場合、この範囲は広告を含む VOD コンテンツ範囲全体です。
* ライブ/リニアの場合、この範囲はシーク可能な時間を表します。

API について詳しくは、 [iOS API リファレンス用 TVSDK 3.4](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v3/index.html)

<!--<a id="example_A153BE3AC03F43C6BF3A156316A08CD3"></a>-->

```
CMTimeRange seekableRange = self.player.seekableRange;  
if (CMTIMERANGE_IS_VALID(seekableRange)) { 
    double start = CMTimeGetSeconds(seekableRange.start);  
    double duration = CMTimeGetSeconds(seekableRange.duration); 
}
```
