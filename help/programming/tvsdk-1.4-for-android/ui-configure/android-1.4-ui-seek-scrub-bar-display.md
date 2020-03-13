---
description: TVSDKは、ビデオオンデマンド(VOD)とライブストリームの両方で、ストリームがスライディングウィンドウプレイリストである特定の位置（時間）のシークをサポートします。
seo-description: TVSDKは、ビデオオンデマンド(VOD)とライブストリームの両方で、ストリームがスライディングウィンドウプレイリストである特定の位置（時間）のシークをサポートします。
seo-title: シークスクラブバーを現在の再生位置で表示
title: シークスクラブバーを現在の再生位置で表示
uuid: a9f4dd6c-78cf-455c-8c31-b2f7b740d84a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# シークスクラブバーを現在の再生位置で表示 {#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDKは、ビデオオンデマンド(VOD)とライブストリームの両方で、ストリームがスライディングウィンドウプレイリストである特定の位置（時間）のシークをサポートします。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVRでのみ許可されます。

1. シーク用のコールバックを設定します。

       シークは非同期なので、TVSDKは以下のシーク関連イベントをディスパッチします。
   
   * `QOSEventListener.onSeekStart`  — シーク開始。
   * `QOSEventListener.onSeekComplete`  — シークに成功しました。
   * `QOSEventListener.onOperationFailed`  — シークに失敗しました。

1. プレイヤーがシーク可能な状態になるのを待ちます。

   有効な状態は、PREPARED、COMPLETE、PAUSEDおよびPLAYINGです。

1. ネイティブのSeekBarを使用して、ユーザ `OnSeekBarChangeListener` ーがスクラブ中のタイミングを確認します。
1. 適切な対応を `QOSEventListener.onOperationFailed` 行い、リッスンします。

   このイベントは、適切な警告を渡します。 アプリケーションは、シークを再試行したり、前の位置から再生を続けたりするなどして、続行する方法を決定します。

1. TVSDKがコールバックを呼び出すまで待 `QOSEventListener.onSeekComplete` ちます。
1. コールバックのpositionパラメーターを使用して、最終的に調整された再生位置を取得します。

   シーク後の実際の開始位置が要求された位置と異なる場合があるので、これは重要です。 広告の時間の途中でシークや他の位置の変更が行われたり、広告の時間をスキップしたりすると、再生動作が影響を受ける場合があります。

1. シークスクラブバーを表示する際は、位置情報を使用します。

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**シークの例**

この例では、ユーザーはシークバーをスクラブして目的の位置をシークします。

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

