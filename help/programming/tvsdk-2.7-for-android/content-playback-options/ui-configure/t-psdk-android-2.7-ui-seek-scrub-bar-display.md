---
description: TVSDKは、スライディングウィンドウプレイリストのストリームである特定の位置（時間）のシーク、ビデオオンデマンド(VOD)およびライブストリームをサポートしています。
seo-description: TVSDKは、スライディングウィンドウプレイリストのストリームである特定の位置（時間）のシーク、ビデオオンデマンド(VOD)およびライブストリームをサポートしています。
seo-title: シークスクラブバーに現在の再生位置を表示
title: シークスクラブバーに現在の再生位置を表示
uuid: df045a10-8d74-4874-8fa5-7e9571c8678d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# シークスクラブバーに現在の再生位置{#display-a-seek-scrub-bar-with-the-current-playback-position}を表示

TVSDKは、スライディングウィンドウプレイリストのストリームである特定の位置（時間）のシーク、ビデオオンデマンド(VOD)およびライブストリームをサポートしています。

>[!TIP]
>
>ライブストリームでのシークは、DVRでのみ可能です。

1. シーク用のコールバックを設定します。

       シークは非同期的なので、TVSDKは以下のシーク関連イベントをディスパッチします。
   
   * `MediaPlayerEvent.SEEK_BEGIN`、seek開始ーの場所。
   * `MediaPlayerEvent.SEEK_END`に設定されている場合、シークが成功したとき。
   * `MediaPlayerEvent.OPERATION_FAILED`に設定され、シークに失敗した場合。

1. プレイヤーがシーク可能なステータスになるのを待ちます。

   有効なステータスは、PREPARED、COMPLETE、PAUSEDおよびPLAYINGです。
1. ネイティブの`SeekBar`を使用して`OnSeekBarChangeListener`を設定します。これはユーザーがスクラブしているタイミングを決定します。
1. 要求されたシーク位置（ミリ秒）を`MediaPlayer.seek`メソッドに渡します。

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   アセットのシーク可能な時間内でのみシークできます。 ビデオオンデマンドの場合、0 ～アセットの長さ。

   >[!TIP]
   >
   >このステップでは、再生ヘッドがストリーム内の新しい位置に移動しますが、計算された最後の位置は、指定されたシーク位置と異なる場合があります。

1. `MediaPlayerEvent.OPERATION_FAILED`をリッスンし、適切な処置を取ります。

   このイベントは、適切な警告を渡します。 続行方法はアプリケーションによって決まります。シークを再試行するか、前の位置から再生を続行するかなどのオプションがあります。

1. TVSDKが`MediaPlayerEvent.SEEK_END`コールバックを呼び出すまで待ちます。
1. コールバックの位置パラメーターを使用して、最後に調整された再生位置を取得します。

   シーク後の実際の開始位置が、要求された位置と異なる場合があるので、これは重要です。 シークや他の位置変更が広告の時間の途中で終了したり、広告の時間をスキップしたりすると、再生動作を含むルールが影響を受ける場合があります。

1. シークスクラブバーを表示する場合は、位置情報を使用します。

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**シークの例**

この例では、ユーザーはシークバーを使用して目的の位置にシークします。

```java
//Use the native SeekBar to set an OnSeekBarChangeListener to 
// see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) { 
            // Update the seek bar thumb with the position provided by the user. 
            setPosition(progress); 
        } 
    } 
 
    @Override 
    public void onStartTrackingTouch(SeekBar seekBar) { 
        isSeeking = true; 
    } 
 
    @Override 
    public void onStopTrackingTouch(SeekBar seekBar) { 
        isSeeking = false; 
 
        // Retrieve the playback range. 
        TimeRange playbackRange = mediaPlayer.getPlaybackRange(); 
 
        // Make sure to seek inside the playback range. 
        long seekPosition = Math.min(Math.round(seekBar.getProgress()), 
        playbackRange.getDuration()); 
     
        // Perform seek. 
        seek(playbackRange.getBegin() + seekPosition); 
    } 
}; 
```

