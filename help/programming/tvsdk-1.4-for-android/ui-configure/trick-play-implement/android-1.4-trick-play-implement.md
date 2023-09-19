---
description: メディアを早送りまたは巻き戻しする場合、ユーザーはトリック再生モードになります。 トリック再生モードに入るには、 MediaPlayer の再生速度を 1 以外の値に設定する必要があります。
title: 早送りと巻き戻しの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# 概要 {#implement-fast-forward-and-rewind-overview}

メディアを早送りまたは巻き戻しする場合、ユーザーはトリック再生モードになります。 トリック再生モードに入るには、 MediaPlayer の再生速度を 1 以外の値に設定する必要があります。

速度を切り替えるには、1 つの値を設定する必要があります。

1. 通常の再生モード (1 x) から、 `MediaPlayer` を使用して、値を設定できます。

   * The `MediaPlayerItem` クラスは、許可される再生レートを定義します。
   * 指定されたレートが許可されていない場合、 TVSDK は許可されている最も近いレートを選択します。

   この例では、プレーヤーの内部再生率を、要求された率に設定します。

   ```java
   import com.adobe.mediacore.MediaPlayer; 
   import com.adobe.mediacore.MediaPlayerItem; 
   import com.adobe.mediacore.MediaPlayerException; 
   import java.util.List; 
   import java.lang.Float; 
   
   private boolean setPlaybackRate(MediaPlayer player, float rate) throws MediaPlayerException  
   { 
       //Get list of playback rates that the media player supports 
       MediaPlayerItem item = player.getCurrentItem(); 
       if(item == null) return false; 
       List<Float> availableRates = player.getCurrentItem().getAvailablePlaybackRates(); 
   
       //Return false if requested rate is not supported 
       if(availableRates.indexOf(rate) == -1) return false; 
   
       //Otherwise set the playback rate to the requested rate  
       //(this can throw MediaPlayerException) 
       player.setRate(rate); 
       return true; 
   }
   ```

1. オプションで、レート変更イベントをリッスンできます。このイベントを使用して、レート変更のリクエストを行った日時や、レート変更が実際に発生した日時を通知できます。

       TVSDK は、トリック再生に関連する以下のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` 時に `rate` の値が別の値に変更された場合。

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` 選択した速度で再生が再開されたとき。

     TVSDK は、プレーヤーがトリック再生モードから通常再生モードに戻ると、これらの両方のイベントをディスパッチします。
