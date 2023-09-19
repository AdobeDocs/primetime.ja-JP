---
description: ビデオの現在の再生位置を保存し、後のセッションで同じ位置で再生を再開できます。
title: ビデオの位置を保存し、後で再開します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ビデオの位置を保存し、後で再開します {#save-the-video-position-and-resume-later}

ビデオの現在の再生位置を保存し、後のセッションで同じ位置で再生を再開できます。

動的に挿入される広告は、ユーザーセッション間で異なるので、位置を保存します **次を使用** スプライスされた広告は、将来のセッションでの異なる位置を指します。 TVSDK は、スライスされた広告を無視して再生位置を取得するメソッドを提供します。

1. ユーザーがビデオを終了すると、アプリケーションはビデオ内の位置を取得して保存します。

   >[!TIP]
   >
   >広告の期間は含まれません。

   広告の時間は、広告パターンや頻度キャップなどによって、セッションごとに異なる場合があります。 あるセッションでのビデオの現在の時刻は、将来のセッションで異なる場合があります。 ビデオ内の位置を保存する際に、アプリケーションはローカル時間を取得し、デバイス上またはサーバー上のデータベースに保存できます。

   例えば、ユーザーがビデオの 20 分目にいて、この位置に 5 分の広告が含まれている場合、 `getCurrentTime` は 1200 秒を返しますが、 `getLocalTime` この位置では、900 秒が返されます。

   >[!IMPORTANT]
   >
   >ライブ/リニアストリームのローカル時間と現在時間は同じです。 この場合、 `convertToLocalTime` 効果はありません。 VOD の場合、広告が再生される間、ローカル時間は変更されません。

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

1. プレーヤーのアクティビティが再開されたら、ユーザーセッションを復元します。

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

   * 以前のセッションで保存された位置からビデオの再生を再開するには、 `seekToLocalTime`.

     >[!TIP]
     >
     >このメソッドは、ローカル時間値でのみ呼び出されます。 現在の時間の結果でメソッドを呼び出した場合、誤った動作が発生します。

   * 現在の時間をシークするには、 `seek`.

1. アプリケーションが `onStatusChanged` ステータス変更イベント。保存されたローカル時間をシークします。

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
1. を実装してユーザーに提示する必要がある広告の時間を提供する `selectAdBreaksToPlay`.

   このメソッドは、ローカル時間の位置より前のプリロール広告ブレークとミッドロール広告ブレークを含みます。 アプリケーションで、プリロール広告ブレークを再生し、指定したローカル時間に再開する、ミッドロール広告ブレークを再生して指定したローカル時間に再開する、または広告ブレークを再生しない、のいずれかを決定できます。
