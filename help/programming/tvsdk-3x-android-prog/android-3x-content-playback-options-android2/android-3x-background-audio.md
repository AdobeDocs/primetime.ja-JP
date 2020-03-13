---
seo-title: バックグラウンドオーディオの有効化
title: バックグラウンドオーディオの有効化
uuid: aa6dc934-e85c-4db1-901b-9777f47106e6
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

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
