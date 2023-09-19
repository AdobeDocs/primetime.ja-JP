---
description: メディアを早送りまたは巻き戻しする場合、ユーザーはトリック再生モードになります。 トリック再生モードに入るには、 MediaPlayer の再生速度を 1 以外の値に設定します。
title: 早送りと巻き戻しの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# 概要 {#implement-fast-forward-and-rewind-overview}

メディアを早送りまたは巻き戻しする場合、ユーザーはトリック再生モードになります。 トリック再生モードに入るには、 MediaPlayer の再生速度を 1 以外の値に設定します。

速度を切り替えるには、1 つの値を設定する必要があります。

1. 通常の再生モード (1 x) から、 `MediaPlayer` を使用して、値を設定できます。

       次の情報に留意してください。
   
   * The `MediaPlayerItem` クラスは、許可される再生レートを定義します。
   * 指定されたレートが許可されていない場合、 TVSDK は許可されている最も近いレートを選択します。

     次の例では、プレーヤーの内部再生率を要求された率に設定します。

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

1. オプションで、レート変更イベントをリッスンできます。このイベントは、レート変更を要求したときと、レート変更が実際に発生したときに通知します。

       TVSDK は、トリック再生に関連する以下のイベントをディスパッチします。
   
   * `MediaPlayerEvent.RATE_SELECTED`、 `rate` の値が別の値に変更された場合。

   * `MediaPlayerEvent.RATE_PLAYING`（選択した速度で再生が再開された場合）

     TVSDK は、プレーヤーがトリック再生モードから通常再生モードに戻ると、これらのイベントをディスパッチします。
