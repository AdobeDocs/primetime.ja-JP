---
title: バックグラウンドオーディオを有効にする
description: バックグラウンドオーディオを有効にする
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# バックグラウンドオーディオを有効にする {#enable-background-audio}

アプリがバックグラウンドになっているときにオーディオ再生を有効にするには、アプリがを呼び出す必要があります `enableAudioPlaybackInBackground` プレーヤーが PREPARED 状態の場合に、引数に true を持つ MediaPlayer の API。

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

アプリは、電話への応答などのイベント中にオーディオフォーカスの保留が解除された場合、再生を一時停止する必要があります。 次のコードスニペットは、 `OnAudioFocusChangeListener`:

```
/** 
 * Register the AudioFocus Change listener to track Audio focus from device. 
 */ 
 AudioManager.OnAudioFocusChangeListener onAudioFocusChangeListener = new AudioManager.OnAudioFocusChangeListener(){ 
     @Override 
     public void onAudioFocusChange(int focusChange){ 
          switch(focusChange){ 
               case AudioManager.AUDIOFOCUS_GAIN: 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT_CAN_DUCK: 
                    /* lower output volume*/ 
                    break; 
               case AudioManager.AUDIOFOCUS_LOSS: 
               case AudioManager.AUDIOFOCUS_LOSS_TRANSIENT: 
                    if(_lastKnownStatus ==MediaPlayerStatus.PLAYING) 
                         _mediaPlayer.pause(); 
                    break; 
          } 
     } 
}; 
 
AudioManager audioManager = (AudioManager) getActivity().getApplicationContext().getSystemService(Context.AUDIO_SERVICE); 
audioManager.requestAudioFocus(onAudioFocusChangeListener, AudioManager.STREAM_MUSIC, AudioManager.AUDIOFOCUS_GAIN);
```
