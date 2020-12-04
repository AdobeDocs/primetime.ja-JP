---
description: デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)のライブメディア開始が発生します。
seo-description: デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)のライブメディア開始が発生します。
seo-title: 特定の時間にストリームを開始
title: 特定の時間にストリームを開始
uuid: f58d908a-77b9-465f-b3a9-8fe63a249d39
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 1%

---


# 特定の時刻にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)のライブメディア開始が発生します。

`MediaPlayer.prepareToPlay`に位置を渡します。

TVSDKは、指定された位置をアセットの開始点と見なします。 シーク操作は必要ありません。 位置がシーク可能な範囲内にない場合は、デフォルトの位置が使用されます。

例：

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
