---
description: TVSDKは、ストリームがスライディングウィンドウプレイリストである特定の位置（時間）のシーク、ビデオオンデマンド(VOD)およびライブストリームをサポートします。
seo-description: TVSDKは、ストリームがスライディングウィンドウプレイリストである特定の位置（時間）のシーク、ビデオオンデマンド(VOD)およびライブストリームをサポートします。
seo-title: シークスクラブバーを現在の再生位置で表示
title: シークスクラブバーを現在の再生位置で表示
uuid: 30a9237c-bbd5-457e-a93c-662570711986
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# シークスクラブバーを現在の再生位置で表示 {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDKは、ストリームがスライディングウィンドウプレイリストである特定の位置（時間）のシーク、ビデオオンデマンド(VOD)およびライブストリームをサポートします。

>[!TIP]
>
>ライブストリームでのシークは、DVRでのみ許可されます。

1. シーク用のコールバックを設定します。

   シークは非同期なので、TVSDKは以下のシーク関連イベントをディスパッチします。

   * `MediaPlayerEvent.SEEK_BEGIN`（シークが開始する場所）。
   * `MediaPlayerEvent.SEEK_END`の場合、シークが成功します。
   * `MediaPlayerEvent.OPERATION_FAILED`に含まれない場合、シークに失敗しました。

1. プレイヤーがシーク可能なステータスになるまで待ちます。

   有効なステータスは、PREPARED、COMPLETE、PAUSEDおよびPLAYINGです。
1. 設定にはネイティブ `SeekBar` を使用しま `OnSeekBarChangeListener`す。この設定によって、ユーザーがスクラブするタイミングが決まります。
1. 要求されたシーク位置（ミリ秒）をメソッドに渡 `MediaPlayer.seek` します。

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   シークできるのは、アセットのシーク可能な時間内だけです。 ビデオオンデマンドの場合、0 ～アセットの期間。

   >[!TIP]
   >
   >この手順では、再生ヘッドをストリーム内の新しい位置に移動しますが、最終的に計算された位置は、指定されたシーク位置と異なる場合があります。

1. 適切な対応を `MediaPlayerEvent.OPERATION_FAILED` 行い、リッスンします。

   このイベントは、適切な警告を渡します。 続行方法はアプリケーションによって決まります。オプションには、シークを再試行する、または前の位置から再生を続行するなどがあります。

1. TVSDKがコールバックを呼び出すまで待 `MediaPlayerEvent.SEEK_END` ちます。
1. コールバックのpositionパラメーターを使用して、最終的に調整された再生位置を取得します。

   シーク後の実際の開始位置が要求された位置と異なる場合があるので、これは重要です。 広告の時間の途中でシークや他の位置変更が行われたり、広告の時間をスキップしたりすると、再生動作を含むルールが影響を受ける場合があります。

1. シークスクラブバーを表示する際は、位置情報を使用します。

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**シークの例**

この例では、ユーザーはシークバーをスクラブして目的の位置をシークします。

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
