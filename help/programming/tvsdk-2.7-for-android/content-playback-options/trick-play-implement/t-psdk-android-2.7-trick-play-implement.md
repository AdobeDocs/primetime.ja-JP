---
description: ユーザーがメディアを早送りまたは巻き戻しすると、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定します。
seo-description: ユーザーがメディアを早送りまたは巻き戻しすると、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定します。
seo-title: 早送りと巻き戻しの実装
title: 早送りと巻き戻しの実装
uuid: 070a3331-43a3-4517-9cd9-06d817ffcfbd
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 概要 {#implement-fast-forward-and-rewind-overview}

ユーザーがメディアを早送りまたは巻き戻しすると、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定します。

速度を切り替えるには、1つの値を設定する必要があります。

1. レートを許容値に設定して、通常再生モード(1x)からトリック再生モ `MediaPlayer` ードに移動します。

       次の情報を記憶しておきます。
   
   * クラス `MediaPlayerItem` は、許可される再生速度を定義します。
   * TVSDKは、指定されたレートが許可されない場合に、最も近い許容レートを選択します。

      次の例では、プレーヤーの内部再生速度を要求された速度に設定します。

      ```
      import com.adobe.mediacore.MediaPlayer; 
      import com.adobe.mediacore.MediaPlayerItem; 
      import com.adobe.mediacore.MediaPlayerException; 
      import java.util.List; 
      import java.lang.Float; 
      
      private boolean setPlaybackRate(MediaPlayer player, float rate)  
        throws MediaPlayerException { 
          // Get list of playback rates that the media player supports 
          MediaPlayerItem item = player.getCurrentItem(); 
          if (item == null) return false; 
          List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
      
          // Return false if requested rate is not supported 
          if (availableRates.indexOf(rate) == -1) return false; 
      
          // Otherwise set the playback rate to the requested rate  
          // (this can throw MediaPlayerException) 
          player.setRate(rate); 
          return true; 
      }
      ```

1. オプションで、レート変更イベントをリッスンできます。このイベントは、レート変更を要求したときとレート変更が実際に発生したときに通知されます。

       TVSDKは、トリック再生に関連する次のイベントをディスパッチします。
   
   * `MediaPlayerEvent.RATE_SELECTED`の値が別の値 `rate` に変更された場合。

   * `MediaPlayerEvent.RATE_PLAYING`を返します。

      TVSDKは、プレーヤーがトリック再生モードから通常再生モードに戻ると、これらのイベントをディスパッチします。

