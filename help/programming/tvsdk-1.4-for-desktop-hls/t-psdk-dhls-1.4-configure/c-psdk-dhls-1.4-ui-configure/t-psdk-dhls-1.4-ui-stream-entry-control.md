---
description: デフォルトでは、再生を開始すると、VODメディアは0から、ライブメディアはクライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)からそれぞれ開始されます。
seo-description: デフォルトでは、再生を開始すると、VODメディアは0から、ライブメディアはクライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)からそれぞれ開始されます。
seo-title: 特定の時間にストリームを入力
title: 特定の時間にストリームを入力
uuid: f58d908a-77b9-465f-b3a9-8fe63a249d39
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# 特定の時間にストリームを入力{#enter-a-stream-at-a-specific-time}

デフォルトでは、再生を開始すると、VODメディアは0から、ライブメディアはクライアントのライブポイント(DefaultMediaPlayer.LIVE_POINT)からそれぞれ開始されます。

に位置を渡します `MediaPlayer.prepareToPlay`。

TVSDKは、指定された位置をアセットの開始ポイントと見なします。 シーク操作は不要です。 位置がシーク可能な範囲内にない場合、はデフォルトの位置を使用します。

例：

```
var seekableRange:TimeRange=_mediaPlayer.seekableRange; 
if (seekableRange.contains(desiredSeekPosition) { 
    _mediaPlayer.seek(desiredSeekPosition); 
}
```
