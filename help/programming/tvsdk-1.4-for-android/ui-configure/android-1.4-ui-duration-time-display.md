---
description: TVSDK を使用して、シークバーに表示できるメディアに関する情報を取得できます。
title: ビデオの長さ、現在時間および残り時間を表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ビデオの長さ、現在時間および残り時間を表示{#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDK を使用して、シークバーに表示できるメディアに関する情報を取得できます。

1. プレーヤーが PREPARED 状態になるのを待ちます。
1. を使用して、現在の再生ヘッド時間を取得する `MediaPlayer.getCurrentTime` メソッド。

   これは、仮想タイムライン上の現在の再生ヘッドの位置をミリ秒単位で返します。 時間は、メインストリームにスプライスされる複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある、解決されたストリームを基準に計算されます。 ライブ/リニアストリームの場合、返される時間は常に再生ウィンドウの範囲にあります。

   ```java
   long getCurrentTime() throws IllegalStateException;
   ```

1. ストリームの再生範囲を取得し、時間を決定します。
   1. 以下を使用します。 `mediaPlayer.getPlaybackRange` メソッドを使用して、仮想タイムラインの時間範囲を取得します。

      ```java
      TimeRange getPlaybackRange() throws IllegalStateException;
      ```

   1. を使用して時間範囲を解析 `mediacore.utils.TimeRange`.
   1. 期間を指定するには、範囲の終わりから開始を引きます。

      これには、ストリームに挿入される追加コンテンツ（広告）の期間が含まれます。

      VOD の場合、範囲は常に 0 で始まり、終了値は、ストリーム（広告）に挿入される追加コンテンツの時間とメインコンテンツの時間の合計に等しくなります。

      リニア/ライブアセットの場合、範囲は再生ウィンドウの範囲を表し、この範囲は再生中に変更されます。

      TVSDK が `onUpdated` メディアアイテムが更新され、その属性（再生範囲を含む）が更新されたことを示すコールバック。

1. で使用できるメソッドの使用 `MediaPlayer` そして `SeekBar` Android SDK でシークバーパラメーターを設定するために一般的に使用可能なクラス。

   例えば、次に示すのは、 `SeekBar` と 2 `TextView` 要素。

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

1. タイマーを使用して、現在の時間を定期的に取得し、SeekBar を更新します。

   次の例では、 `Clock.java` タイマーとしてのヘルパークラス。リファレンスプレーヤーの PrimetimeReference で使用できます。 このクラスはイベントリスナーを設定し、トリガーを `onTick` イベントを 1 秒ごと、または指定可能な別のタイムアウト値。

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

   この例では、時計のたびに、メディアプレーヤーの現在の位置を取得し、SeekBar を更新します。 2 つの TextView 要素を使用して、現在時間と再生範囲の終了位置を数値としてマークします。

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
