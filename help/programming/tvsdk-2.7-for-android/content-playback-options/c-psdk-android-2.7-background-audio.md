---
title: バックグラウンドオーディオを有効にする
description: バックグラウンドオーディオを有効にする
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# バックグラウンドオーディオを有効にする{#enable-background-audio}

アプリがバックグラウンドにあるときのオーディオ再生を有効にするには、プレイヤーがPREPARED状態のときに、アプリはMediaPlayerの`enableAudioPlaybackInBackground` APIを引数としてtrueで呼び出す必要があります。

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

アプリは、電話への応答などのイベント中に、オーディオのフォーカスが保持されなくなった場合、再生を一時停止する必要があります。 次のコードスニペットは、`OnAudioFocusChangeListener`の実装方法を示しています。

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

