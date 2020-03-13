---
description: ユーザーが広告をクリックすると、アプリケーションはメインビデオコンテンツの再生を一時停止する必要があります。
seo-description: ユーザーが広告をクリックすると、アプリケーションはメインビデオコンテンツの再生を一時停止する必要があります。
seo-title: 再生の一時停止と再開
title: 再生の一時停止と再開
uuid: 87ba9f05-912d-4b85-8add-feb26a796a3a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 再生の一時停止と再開 {#pause-and-resume-playback}

ユーザーが広告をクリックすると、アプリケーションはメインビデオコンテンツの再生を一時停止する必要があります。

1. Androidアクティビテ `onPause` ィのおよ `onResume` びを上書きします。

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

