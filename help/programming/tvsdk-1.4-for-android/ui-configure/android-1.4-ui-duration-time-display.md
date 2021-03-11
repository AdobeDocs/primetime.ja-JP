---
description: TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。
title: ビデオの長さ、現在時間および残り時間の表示
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# ビデオの長さ、現在時間、残り時間の表示{#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。

1. プレイヤーがPREPARED状態になるのを待ちます。
1. `MediaPlayer.getCurrentTime`メソッドを使用して、再生ヘッドの現在の時間を取得します。

   これは、仮想タイムライン上の再生ヘッドの現在の位置をミリ秒単位で返します。 時間は、メインストリームにスライスされる複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある、解決済みストリームを基準にして計算されます。 ライブ/リニアストリームの場合、戻り時間は常に再生時間の範囲にあります。

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. ストリームの再生範囲を取得し、長さを決定します。
   1. `mediaPlayer.getPlaybackRange`メソッドを使用して、バーチャルタイムラインの時間範囲を取得します。

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. `mediacore.utils.TimeRange`を使用して時間範囲を解析します。
   1. 長さを調べるには、範囲の終わりから開始を引きます。

      これには、ストリームに挿入される追加コンテンツ（広告）の長さも含まれます。

      VODの場合、範囲は常に0で始まり、終了値はメインコンテンツの長さと、ストリームに挿入される追加コンテンツ（広告）の長さの合計と等しくなります。

      リニア/ライブアセットの場合、範囲は再生時間の範囲を表し、再生中にこの範囲が変わります。

      TVSDKは、`onUpdated`コールバックを呼び出して、メディア項目が更新され、その属性（再生範囲を含む）が更新されたことを示します。

1. `MediaPlayer`で使用できるメソッドと、Android SDKでpublicクラスとして有効な`SeekBar`クラスを使用して、シークバーパラメーターを設定します。

   例えば、`SeekBar`と2つの`TextView`要素を含むレイアウトを次に示します。

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

1. タイマーを使用して、定期的に現在時間を取得し、SeekBarを更新します。

   次の例では、`Clock.java`ヘルパークラスをタイマーとして使用します。このタイマーは、参照プレーヤーPrimetimeReferenceで使用できます。 このクラスは、イベントリスナーとトリガーに対して、1秒ごとに`onTick`イベントを設定するか、別のタイムアウト値を指定します。

   ```java
   playbackClock = new Clock(PLAYBACK_CLOCK, CLOCK_TIMER); 
   playbackClockEventListener = new Clock.ClockEventListener() { 
   @Override 
   public void onTick(String name) { 
       // Timer event is received. Update the SeekBar here. 
   } 
   }; 
   playbackClock.addClockEventListener(playbackClockEventListener);
   ```

   この例では、時計が鳴るたびに、メディアプレイヤーの現在の位置を取得し、SeekBarを更新します。 2つのTextView要素を使用して、現在時間と再生範囲の終了位置を数値でマークします。

   ```java
   @Override 
   public void onTick(String name) { 
   if (mediaPlayer != null && mediaPlayer.getStatus() == PlayerState.PLAYING) { 
       handler.post(new Runnable() { 
           @Override 
           public void run() { 
               seekBar.setProgress((int)  
                    mediaPlayer.getCurrentTime()); 
               currentTimeText.setText(timeStampToText( 
                  mediaPlayer.getCurrentTime())); 
               totalTimeText.setText(timeStampToText( 
                   mediaPlayer.getPlaybackRange().getEnd())); 
           } 
       }); 
   } 
   }
   ```

