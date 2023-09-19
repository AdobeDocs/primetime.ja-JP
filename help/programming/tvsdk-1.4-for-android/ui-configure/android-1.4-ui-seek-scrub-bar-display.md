---
description: TVSDK は、ビデオオンデマンド (VOD) とライブストリームの両方で、ストリームがスライドウィンドウプレイリストである特定の位置（時間）へのシークをサポートしています。
title: シークスクラブバーを現在の再生位置で表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# シークスクラブバーを現在の再生位置で表示 {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK は、ビデオオンデマンド (VOD) とライブストリームの両方で、ストリームがスライドウィンドウプレイリストである特定の位置（時間）へのシークをサポートしています。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVR でのみ許可されます。

1. シークのコールバックを設定します。

       シークは非同期なので、 TVSDK は以下のシーク関連イベントをディスパッチします。
   
   * `QOSEventListener.onSeekStart`  — シーク開始。
   * `QOSEventListener.onSeekComplete`  — シークに成功しました。
   * `QOSEventListener.onOperationFailed`  — シークに失敗しました。

1. プレーヤーがシーク可能な状態になるのを待ちます。

   有効な状態は、準備済み、完了、一時停止および再生です。

1. ネイティブの SeekBar を使用して設定 `OnSeekBarChangeListener` をクリックして、ユーザーがスクラブしている時間を確認します。
1. 次をリッスン： `QOSEventListener.onOperationFailed` 適切な行動を取る。

   このイベントは、適切な警告を渡します。 例えば、シークを再試行したり、前の位置から再生を続行したりすることで、アプリケーションの進め方が決まります。

1. TVSDK が `QOSEventListener.onSeekComplete` コールバック。
1. コールバックの position パラメーターを使用して、最後に調整された再生位置を取得します。

   シーク後の実際の開始位置は、リクエストされた位置と異なる場合があるので、これは重要です。 シークやその他の再配置が広告の途中で終了したり、広告の時間をスキップしたりすると、再生動作が影響を受ける場合があります。

1. シークスクラブバーを表示する際には、位置情報を使用します。

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**シークの例**

この例では、ユーザーはシークバーをスクラブして、目的の位置を探します。

```java
// Use the native SeekBar to set OnSeekBarChangeListener to  
//see when the user is scrubbing. 
seekBar.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() { 
 
    @Override 
    public void onProgressChanged(SeekBar seekBar, int progress, boolean isFromUser) { 
        if (isFromUser) {  
            // Update the seek bar thumb, with the position provided by the user. 
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
