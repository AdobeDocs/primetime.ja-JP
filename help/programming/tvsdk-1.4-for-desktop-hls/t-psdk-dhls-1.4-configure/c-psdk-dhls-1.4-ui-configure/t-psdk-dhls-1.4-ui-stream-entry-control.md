---
description: デフォルトでは、再生を開始すると、0のVODメディア開始と、クライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)のライブメディア開始が発生します。
title: 特定の時間にストリームを開始
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 2%

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
