---
description: ユーザーが広告をクリックすると、アプリケーションは、メインビデオコンテンツの再生を一時停止する必要があります。
title: 再生の一時停止と再開
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# 再生の一時停止と再開{#pause-and-resume-playback}

ユーザーが広告をクリックすると、アプリケーションは、メインビデオコンテンツの再生を一時停止する必要があります。

Androidアクティビティの`onPause`と`onResume`を上書きします。

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

