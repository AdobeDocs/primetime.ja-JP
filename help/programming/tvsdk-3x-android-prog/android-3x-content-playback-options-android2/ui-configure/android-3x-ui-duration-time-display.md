---
description: TVSDKを使用して、メディア内でのプレイヤーの位置に関する情報を取得し、シークバーに表示できます。
seo-description: TVSDKを使用して、メディア内でのプレイヤーの位置に関する情報を取得し、シークバーに表示できます。
seo-title: ビデオの長さ、現在時間、残り時間を表示します
title: ビデオの長さ、現在時間、残り時間を表示します
uuid: 29bb6bc2-dab1-4f35-abcf-d3213605ee70
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# ビデオの長さ、現在時間、残り時間を表示します {#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDKを使用して、メディア内でのプレイヤーの位置に関する情報を取得し、シークバーに表示できます。

1. プレイヤーがPREPARED状態以上になるまで待ちます。
1. メソッドを使用して、現在の再生ヘッドの時間を取得 `MediaPlayer.getCurrentTime` します。

   仮想タイムライン上の現在の再生ヘッドの位置をミリ秒単位で返します。 時間は、メインストリームにスライスされた複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある解決済みストリームを基準にして計算されます。 ライブ/リニアストリームの場合、戻り時間は常に再生時間の範囲に含まれます。

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. ストリームの再生範囲を取得し、時間を指定します。
   1. このメソッドを `MediaPlayer.getPlaybackRange` 使用して、バーチャルタイムラインの時間範囲を取得します。

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. このメソッドを `MediaPlayer.getPlaybackRange` 使用して、バーチャルタイムラインの時間範囲を取得します。

      * VODの場合、範囲は常に0で始まり、終了値はメインコンテンツの長さとストリーム（広告）内の追加コンテンツの長さの合計と等しくなります。
      * リニア/ライブアセットの場合、範囲は再生ウィンドウの範囲を表します。 この範囲は再生中に変更されます。

         TVSDKがこのコールバックを `ITEM_Updated` 呼び出して、メディア項目が更新され、その属性（再生範囲を含む）が更新されたことを示します。

1. Android SDKのクラスで使用でき `MediaPlayer` るメソッド `SeekBar` を使用して、シークバーパラメーターを設定します。

   例えば、シークバーと2つの要素を含むレイアウトを次に示し `TextView` ます。

   ```xml
   <LinearLayout 
    android:id="@+id/controlBarLayout" 
    android:layout_width="match_parent" 
    android:layout_height="wrap_content" 
    android:layout_alignParentBottom="true" 
    android:background="@android:color/black" 
    android:orientation="horizontal" > 
    <TextView 
       android:id="@+id/playerCurrentTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
    <SeekBar 
       android:id="@+id/playerSeekBar" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_weight="1" /> 
    <TextView 
       android:id="@+id/playerTotalTimeText" 
       android:layout_width="wrap_content" 
       android:layout_height="wrap_content" 
       android:layout_margin="7dp" 
       android:text="00:00" 
       android:textColor="@android:color/white" /> 
   </LinearLayout>
   ```

1. 次の図に示すように、タイマーを使用して、現在の時間を定期的に取得し、シークバーを更新します。

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width=&quot;477.000pt&quot;}

   次の例では、で使用で `Clock.java` きるヘルパークラスをタイマーと `ReferencePlayer`して使用しています。 このクラスは、イベントリスナーを設定し、1秒 `onTick` ごと、または指定可能な別のタイムアウト値をトリガーします。

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
       @Override 
       public void onTick(String name) { 
           // Timer event is received. Update the seek bar here. 
       } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   この例では、時計の目盛りが鳴るたびに、メディアプレイヤーの現在の位置を取得し、シークバーを更新します。 2つの要素を使用し `TextView` て、現在時間と再生範囲の終了位置を数値としてマークします。

   ```java
   @Override 
   public void onTick(String name) { 
       if (mediaPlayer != null &&  
         mediaPlayer.getStatus() == MediaPlayerStatus.PLAYING) { 
           handler.post(new Runnable() { 
               @Override 
               public void run() { 
                   seekBar.setProgress((int) mediaPlayer.getCurrentTime()); 
                   currentTimeText.setText(timeStampToText(mediaPlayer.getCurrentTime())); 
                   totalTimeText.setText(timeStampToText(mediaPlayer.getPlaybackRange().getEnd())); 
               } 
           }); 
       } 
   } 
   ```
