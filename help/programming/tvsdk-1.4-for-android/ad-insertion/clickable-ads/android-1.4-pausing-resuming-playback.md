---
description: ユーザーが広告をクリックすると、アプリケーションはメインのビデオコンテンツの再生を一時停止する必要があります。
title: 再生の一時停止と再開
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# 再生の一時停止と再開 {#pause-and-resume-playback}

ユーザーが広告をクリックすると、アプリケーションはメインのビデオコンテンツの再生を一時停止する必要があります。

次を上書き： `onPause` および `onResume` を Android アクティビティから削除します。

```java
@Override 
public void onResume() { 
    super.onResume(); 
    requestAudioFocus(); 
    if (_lastKnownStatus == MediaPlayer.PlayerState.PAUSED) { 
        _mediaPlayer.play(); 
    } 
} 
... 
 
@Override 
public void onPause() { 
    super.onPause(); 
    if (_mediaPlayer != null) { 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING || 
          _mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) { 
            _savedPlayerState = _mediaPlayer.getStatus(); 
            _lastKnownTime = _mediaPlayer.getCurrentTime(); 
        } 
        if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PLAYING) { 
            _mediaPlayer.pause(); 
            _lastKnownStatus = MediaPlayer.PlayerState.PAUSED; 
        } 
    } 
} 
 
abandonAudioFocus(); 
```
