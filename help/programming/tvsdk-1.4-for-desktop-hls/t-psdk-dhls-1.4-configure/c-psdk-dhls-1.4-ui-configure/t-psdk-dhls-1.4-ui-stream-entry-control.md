---
description: デフォルトでは、再生を開始すると、VOD メディアは 0 から、ライブメディアはクライアントのライブポイント (DefaultMediaPlayer.LIVE_POINT) からそれぞれ開始されます。
title: 特定の時間にストリームを入力
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# 特定の時間にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VOD メディアは 0 から、ライブメディアはクライアントのライブポイント (DefaultMediaPlayer.LIVE_POINT) からそれぞれ開始されます。

位置をに渡す `MediaPlayer.prepareToPlay`.

TVSDK は、指定された位置をアセットの開始点と見なします。 シーク操作は必要ありません。 位置がシーク可能な範囲内にない場合、はデフォルトの位置を使用します。

例：

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
