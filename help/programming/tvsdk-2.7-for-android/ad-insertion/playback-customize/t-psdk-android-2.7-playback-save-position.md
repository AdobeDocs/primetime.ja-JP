---
description: 現在の再生位置をビデオ内に保存し、以降のセッションで同じ位置での再生を再開できます。
title: ビデオの位置を保存し、後で再開します
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ビデオの位置を保存して後で再開{#save-the-video-position-and-resume-later}

現在の再生位置をビデオ内に保存し、以降のセッションで同じ位置での再生を再開できます。

動的に挿入される広告は、ユーザーセッション間で異なるので、**を**&#x200B;スライスされた広告と共に保存した場合、以降のセッションでは別の位置が参照されます。 TVSDKは、スライスされた広告を無視して、再生位置を取得するメソッドを提供します。

1. ユーザーがビデオを終了すると、アプリケーションはビデオ内の位置を取得して保存します。

   >[!TIP]
   >
   >広告の時間は含まれません。

   広告の時間は、広告パターン、フリークエンシーキャップなどのため、セッションごとに異なる場合があります。 あるセッションでのビデオの現在時間は、将来のセッションでは異なる場合があります。 ビデオ内の位置を保存すると、ローカル時間が取得され、デバイス上またはサーバー上のデータベースに保存できます。

   例えば、ユーザーがビデオの20分にいて、この位置に5分の広告が含まれている場合、`getCurrentTime`は1200秒を返し、`getLocalTime`は900秒を返します。

   >[!IMPORTANT]
   >
   >ライブ/リニアストリームの場合、ローカル時間と現在時間は同じです。 この場合、`convertToLocalTime`は無効です。 VODの場合、広告が再生されても、ローカル時間は変更されません。

   ```java
   // Save the user session when player activity stops 
       @Override 
       public void onStop(){ 
           super.onStop(); 
           ... 
           prefs = PreferenceManager.getDefaultSharedPreferences( 
                                     getActivity().getApplicationContext()); 
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
       prefs =  
         PreferenceManager.getDefaultSharedPreferences(getActivity().getApplicationContext()); 
       if (prefs.getString(LAST_MEDIA_RESOURCE, "nil"). 
         equals(_contentInfo.toMediaResource().getUrl())) { 
           _lastKnownLocalTime =  
             prefs.getLong(LAST_LOCAL_TIME, 0); // get the last local time  
                                                // saved in system preferences 
           if(_lastKnownLocalTime > 0) { 
               _shouldResumePlayback = true; 
           } 
       } 
       ... 
   } 
   ```

1. ビデオを同じ位置で再開するには：

   * 前のセッションで保存した位置からビデオの再生を再開するには、`seekToLocalTime`を使用します。

      >[!TIP]
      >
      >このメソッドは、ローカル時間値でのみ呼び出されます。 現在の時間でメソッドを呼び出すと、誤った動作が発生します。

   * 現在時間をシークするには、`seek`を使用します。

1. アプリケーションが`onStatusChanged`ステータス変更イベントを受け取ったら、保存済みのローカル時間をシークします。

   ```java
   private final MediaPlayer.PlaybackEventListener _playbackEventListener =  
     new MediaPlayer.PlaybackEventListener() { 
       @Override 
       public void onPrepared() { 
           ... 
           if(_shouldResumePlayback){ 
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
1. `selectAdBreaksToPlay`を実装して、ユーザーに表示する必要のある広告の時間を提供します。

   このメソッドは、ローカル時間位置より前のプリロール広告ブレークとミッドロール広告ブレークを含みます。 アプリケーションで、プリロール広告の時間を再生して指定したローカル時間に再開、ミッドロール広告の時間を再生して指定したローカル時間に再開、または広告の時間を再生しないことを決定できます。
