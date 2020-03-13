---
seo-title: バックグラウンドオーディオの有効化
title: バックグラウンドオーディオの有効化
uuid: 1e7319f5-ee16-47bd-bfd5-d3dcfe69bf4b
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# バックグラウンドオーディオの有効化 {#enable-background-audio}

アプリがバックグラウンドにある場合にオーディオ再生を有効にするには、プレイヤーがPREPARED状態の場合に、アプリはMediaPlayerの `enableAudioPlaybackInBackground` APIを引数としてtrueで呼び出す必要があります。

```
_mediaPlayer.enableAudioPlaybackInBackground(true);
```

電話などに応答するなどのイベント中に、オーディオフォーカスの保留が解除された場合、アプリは再生を一時停止する必要があります。 次のコードスニペットに、を実装する方法を示しま `OnAudioFocusChangeListener`す。

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

