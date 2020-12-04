---
description: メディアを早送りまたは巻き戻しする場合は、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定します。
seo-description: メディアを早送りまたは巻き戻しする場合は、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定します。
seo-title: 早送りと巻き戻しの実装
title: 早送りと巻き戻しの実装
uuid: 070a3331-43a3-4517-9cd9-06d817ffcfbd
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# 概要{#implement-fast-forward-and-rewind-overview}

メディアを早送りまたは巻き戻しする場合は、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定します。

速度を切り替えるには、1つの値を設定する必要があります。

1. `MediaPlayer`の速度を許可値に設定して、通常再生モード(1x)からトリック再生モードに移行します。

       次の情報を覚えておいてください。
   
   * `MediaPlayerItem`クラスは、許可される再生速度を定義します。
   * TVSDKは、指定されたレートが許可されない場合、許可されている最も近いレートを選択します。

      次の例では、プレイヤーの内部再生速度を要求された速度に設定します。

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

1. 必要に応じてレート変更イベントをリッスンできます。このイベントは、レート変更を要求したときやレート変更が実際に発生したときに通知します。

       TVSDKは、トリック再生に関連する次のイベントをディスパッチします。
   
   * `MediaPlayerEvent.RATE_SELECTED`の値が別の値に変更された `rate` 場合。

   * `MediaPlayerEvent.RATE_PLAYING`（選択した速度で再生が再開された場合）。

      TVSDKは、プレイヤーがトリック再生モードから通常再生モードに戻ると、これらのイベントをディスパッチします。

