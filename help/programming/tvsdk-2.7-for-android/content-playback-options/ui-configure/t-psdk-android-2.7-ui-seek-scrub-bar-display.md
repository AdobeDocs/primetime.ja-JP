---
description: TVSDK は、ストリームがスライドウィンドウプレイリストである特定の位置（時間）へのシークをサポートしています ( ビデオオンデマンド (VOD) およびライブストリーム )。
title: シークスクラブバーを現在の再生位置で表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# シークスクラブバーを現在の再生位置で表示 {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK は、ストリームがスライドウィンドウプレイリストである特定の位置（時間）へのシークをサポートしています ( ビデオオンデマンド (VOD) およびライブストリーム )。

>[!TIP]
>
>ライブストリームでのシークは、DVR でのみ許可されます。

1. シークのコールバックを設定します。

       シークは非同期なので、 TVSDK は以下のシーク関連イベントをディスパッチします。
   
   * `MediaPlayerEvent.SEEK_BEGIN`（シークが開始する場所）
   * `MediaPlayerEvent.SEEK_END`（シークが成功した場合）。
   * `MediaPlayerEvent.OPERATION_FAILED`（シークが失敗した場合）

1. プレーヤーがシークの有効なステータスになるのを待ちます。

   有効なステータスは、PREPARED、COMPLETE、PAUSED および PLAYING です。
1. ネイティブのを使用 `SeekBar` 設定する `OnSeekBarChangeListener`：ユーザーがスクラブするタイミングを指定します。
1. 要求されたシーク位置（ミリ秒）を `MediaPlayer.seek` メソッド。

   ```java
   void seek(long position) throws MediaPlayerException;
   ```

   アセットのシーク可能な期間内にのみシークできます。 ビデオオンデマンドの場合は、0 ～アセットの期間です。

   >[!TIP]
   >
   >このステップは、再生ヘッドをストリーム内の新しい位置に移動させますが、最終的に計算された位置は、指定されたシーク位置とは異なる場合があります。

1. 次をリッスン： `MediaPlayerEvent.OPERATION_FAILED` 適切な行動を取る。

   このイベントは、適切な警告を渡します。 続行方法はアプリケーションによって決まります。オプションには、シークを再試行するか、前の位置から再生を続行するかが含まれます。

1. TVSDK が `MediaPlayerEvent.SEEK_END` コールバック。
1. コールバックの position パラメーターを使用して、最後に調整された再生位置を取得します。

   シーク後の実際の開始位置は、リクエストされた位置と異なる場合があるので、これは重要です。 シークやその他の再配置が広告の途中で終了したり、広告の時間をスキップしたりすると、再生動作を含むルールが適用される場合があります。

1. シークスクラブバーを表示する際には、位置情報を使用します。

<!--<a id="example_EEB73818260C43C8B5AE12BA68548AB7"></a>-->

**シークの例**

この例では、ユーザーはシークバーをスクラブして、目的の位置を探します。

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
