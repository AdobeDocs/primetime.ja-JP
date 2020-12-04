---
description: ユーザーが広告をクリックすると、アプリケーションは、メインビデオコンテンツの再生を一時停止する必要があります。
seo-description: ユーザーが広告をクリックすると、アプリケーションは、メインビデオコンテンツの再生を一時停止する必要があります。
seo-title: 再生の一時停止と再開
title: 再生の一時停止と再開
uuid: 229e2499-e30e-458c-bd6d-d035588c21cf
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# 再生の一時停止と再開{#pause-and-resume-playback}

ユーザーが広告をクリックすると、アプリケーションは、メインビデオコンテンツの再生を一時停止する必要があります。

1. Androidアクティビティの`onPause`と`onResume`を上書きします。

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       requestAudioFocus(); 
       if (_lastKnownStatus == MediaPlayerStatus.PAUSED) { 
           _mediaPlayer.play(); 
       } 
   } 
   ... 
   
   @Override 
   public void onPause() { 
       super.onPause(); 
       if (_mediaPlayer != null) { 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING || 
             _mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) { 
               _savedPlayerStatus = _mediaPlayer.getStatus(); 
               _lastKnownTime = _mediaPlayer.getCurrentTime(); 
           } 
           if (_mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
               _mediaPlayer.pause(); 
               _lastKnownStatus = MediaPlayerStatus.PAUSED; 
           } 
       } 
   } 
   abandonAudioFocus(); 
   ```

