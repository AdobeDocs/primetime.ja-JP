---
description: TVSDKを使用して、メディア内でのプレイヤーの位置に関する情報を取得し、シークバーに表示できます。
seo-description: TVSDKを使用して、メディア内でのプレイヤーの位置に関する情報を取得し、シークバーに表示できます。
seo-title: ビデオの長さ、現在時間および残り時間の表示
title: ビデオの長さ、現在時間および残り時間の表示
uuid: 13627fa2-8cd8-4336-bc4b-7e3226330389
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ビデオの長さ、現在時間、残り時間の表示{#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDKを使用して、メディア内でのプレイヤーの位置に関する情報を取得し、シークバーに表示できます。

1. プレイヤーがPREPARED状態以上になるのを待ちます。
1. `MediaPlayer.getCurrentTime`メソッドを使用して、再生ヘッドの現在の時間を取得します。

   これは、仮想タイムライン上の再生ヘッドの現在の位置をミリ秒単位で返します。 時間は、メインストリームにスライスされる複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある、解決済みストリームを基準にして計算されます。 ライブ/リニアストリームの場合、戻り時間は常に再生時間の範囲にあります。

   ```java
   long getCurrentTime() throws MediaPlayerException;
   ```

1. ストリームの再生範囲を取得し、長さを決定します。
   1. `MediaPlayer.getPlaybackRange`メソッドを使用して、バーチャルタイムラインの時間範囲を取得します。

      ```java
      TimeRange getPlaybackRange() throws MediaPlayerException;
      ```

   1. `MediaPlayer.getPlaybackRange`メソッドを使用して、バーチャルタイムラインの時間範囲を取得します。

      * VODの場合、範囲は常に0で始まり、終了値はメインコンテンツの長さとストリーム（広告）内の追加コンテンツの長さの合計になります。
      * リニア/ライブアセットの場合、範囲は再生時間の範囲を表します。 この範囲は再生中に変更されます。

         TVSDKは、`ITEM_Updated`コールバックを呼び出して、メディア項目が更新され、その属性（再生範囲を含む）が更新されたことを示します。

1. Android SDKの`MediaPlayer`および`SeekBar`クラスで使用できるメソッドを使用して、シークバーパラメーターを設定します。

   例えば、シークバーと2つの`TextView`要素を含むレイアウトを次に示します。

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

1. 次の図に示すように、タイマーを使用して、現在時間を定期的に取得し、シークバーを更新します。

   <!--<a id="fig_689CEDDD02094C0C8E91C5195F8EAD3F"></a>-->

   ![](assets/seek-bar.jpg){width=&quot;477.000pt&quot;}

   次の例では、`ReferencePlayer`で使用できる`Clock.java`ヘルパークラスをタイマーとして使用します。 このクラスは、イベントリスナーを設定し、1秒ごとに`onTick`イベントをトリガーします。また、別のタイムアウト値を指定することもできます。

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

   この例では、時計が鳴るたびに、メディアプレイヤーの現在の位置を取得し、シークバーを更新します。 2つの`TextView`要素を使用して、現在時間と再生範囲の終了位置を数値でマークします。

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

