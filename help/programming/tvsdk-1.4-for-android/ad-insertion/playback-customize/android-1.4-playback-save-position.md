---
description: 現在の再生位置をビデオに保存し、今後のセッションで同じ位置での再生を再開できます。
seo-description: 現在の再生位置をビデオに保存し、今後のセッションで同じ位置での再生を再開できます。
seo-title: ビデオの位置を保存し、後で再開します
title: ビデオの位置を保存し、後で再開します
uuid: 322f780d-09ba-44b0-b2e5-46288bf58fda
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ビデオの位置を保存し、後で再開します {#save-the-video-position-and-resume-later}

現在の再生位置をビデオに保存し、今後のセッションで同じ位置での再生を再開できます。

動的に挿入される広告は、ユーザーセッション間で異なるので、スライスされた広告 **での** 「位置」を保存すると、将来のセッションでは別の位置が参照されます。 TVSDKは、スライスされた広告を無視して再生位置を取得するメソッドを提供します。

1. ユーザーがビデオを終了すると、アプリケーションはビデオ内の位置を取得し、保存します。

   >[!TIP]
   >
   >広告の時間は含まれません。

   広告の時間は、広告パターンや周波数制限などによって、セッションごとに異なる場合があります。 あるセッションでのビデオの現在時間は、今後のセッションで異なる場合があります。 ビデオ内の位置を保存すると、アプリケーションはローカル時間を取得し、デバイスまたはサーバー上のデータベースに保存できます。

   例えば、ユーザーがビデオの20分目にいて、この位置に5分の広告が含まれている場合、1200秒が返され、この位置にある場合は `getCurrentTime` 900秒が `getLocalTime` 返されます。

   >[!IMPORTANT]
   >
   >ライブ/リニアストリームの場合、ローカル時間と現在時間は同じです。 この場合、は何も `convertToLocalTime` 影響しません。 VODの場合、広告の再生中、ローカル時間は変更されません。

   ```java
   // Save the user session when player activity stops 
   @Override 
   public void onStop() { 
       super.onStop(); 
       ... 
       prefs = PreferenceManager.getDefaultSharedPreferences( 
                 getActivity().getApplicationContext() 
               ); 
       SharedPreferences.Editor editor = prefs.edit(); 
       // get the local time where stream stopped playing and  
       // save it in System preferences 
       editor.putLong(LAST_LOCAL_TIME, _mediaPlayer.getLocalTime());  
       editor.putString(LAST_MEDIA_RESOURCE, _contentInfo.toMediaResource().getUrl()); 
       editor.commit(); 
       ... 
   } 
   ```

1. プレイヤーのアクティビティが再開されたら、ユーザーセッションを復元します。

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       ... 
       prefs = PreferenceManager.getDefaultSharedPreferences(getActivity().getApplicationContext()); 
       if (prefs.getString(LAST_MEDIA_RESOURCE, "nil").equals(_contentInfo.toMediaResource().getUrl())) { 
   
           _lastKnownLocalTime = prefs.getLong(LAST_LOCAL_TIME, 0);    // get the last local time saved  
                                                                       // in system preferences 
           if (_lastKnownLocalTime > 0) { 
               _shouldResumePlayback = true; 
           } 
       } 
       ... 
   } 
   ```

1. ビデオを同じ位置で再開するには：

   * 前のセッションで保存した位置からビデオの再生を再開するには、を使用しま `seekToLocalTime`す。

      >[!TIP]
      >
      >このメソッドは、ローカル時間値でのみ呼び出されます。 現在の時間でメソッドを呼び出すと、誤った動作が発生します。

   * 現在の時間をシークするには、を使用しま `seek`す。

1. アプリケーションがステータス変更イ `onStatusChanged` ベントを受け取ったら、保存されたローカル時間をシークします。

   ```java
   private final MediaPlayer.PlaybackEventListener _playbackEventListener =  
     new MediaPlayer.PlaybackEventListener() { 
       @Override 
       public void onPrepared() { 
           ... 
           if (_shouldResumePlayback) { 
               if(_lastKnownLocalTime >= 0) { 
                   _mediaPlayer.seekToLocalTime(_lastKnownLocalTime); 
               } 
           } 
           ... 
       } 
        ... 
   } 
   ```

1. 広告ポリシーインターフェイスで指定した広告の時間を提供します。
1. デフォルトの広告ポリシーセレクターを拡張して、カスタム広告ポリシーセレクターを実装します。
1. 実装することでユーザーに表示する必要がある広告の時間を指定しま `selectAdBreaksToPlay`す。

   この方法には、プリロール広告の時間と、ローカル時間の位置より前のミッドロール広告の時間が含まれます。 アプリケーションで、プリロール広告の時間を再生して指定したローカル時間に再開する、ミッドロール広告の時間を再生して指定したローカル時間に再開する、または広告の時間を再生しないことを決定できます。
