---
description: TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。
seo-description: TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。
seo-title: ビデオの長さ、現在時間、残り時間を表示します
title: ビデオの長さ、現在時間、残り時間を表示します
uuid: afb43169-2d82-4137-ba38-27caef3d8c21
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ビデオの長さ、現在時間、残り時間を表示します{#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。

1. プレイヤーがPREPARED状態になるまで待ちます。
1. メソッドを使用して、現在の再生ヘッドの時間を取得 `MediaPlayer.getCurrentTime` します。

   仮想タイムライン上の現在の再生ヘッドの位置をミリ秒単位で返します。 時間は、メインストリームにスライスされた複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある解決済みストリームを基準にして計算されます。 ライブ/リニアストリームの場合、戻り時間は常に再生時間の範囲に含まれます。

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. ストリームの再生範囲を取得し、時間を指定します。
   1. このメソッドを `mediaPlayer.getPlaybackRange` 使用して、バーチャルタイムラインの時間範囲を取得します。

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. を使用して時間範囲を解析しま `mediacore.utils.TimeRange`す。
   1. 期間を指定するには、範囲の終わりから開始値を引きます。

      これには、ストリーム（広告）に挿入される追加コンテンツの長さも含まれます。

      VODの場合、範囲は常に0で始まり、終了値はメインコンテンツの長さと、ストリーム（広告）に挿入される追加コンテンツの長さの合計と等しくなります。

      リニア/ライブアセットの場合、範囲は再生ウィンドウの範囲を表し、この範囲は再生中に変更されます。

      TVSDKがコールバックを `onUpdated` 呼び出して、メディア項目が更新され、その属性（再生範囲を含む）が更新されたことを示します。

1. シークバーパラメーターを設 `MediaPlayer` 定するに `SeekBar` は、Android SDKで公開されている、およびで使用可能なメソッドを使用します。

   例えば、と2つの要素を含むレイアウトを次に `SeekBar` 示し `TextView` ます。

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

1. タイマーを使用して、定期的に現在の時間を取得し、SeekBarを更新します。

   次の例では、ヘルパーク `Clock.java` ラスをタイマーとして使用し、参照プレーヤーPrimetimeReferenceで使用できます。 このクラスは、イベントリスナーを設定し、1秒 `onTick` ごと、または指定可能な別のタイムアウト値をトリガーします。

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

   この例では、時計の目盛りが鳴るたびに、メディアプレイヤーの現在の位置を取得し、SeekBarを更新します。 2つのTextView要素を使用して、現在時間と再生範囲の終了位置を数値としてマークします。

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

