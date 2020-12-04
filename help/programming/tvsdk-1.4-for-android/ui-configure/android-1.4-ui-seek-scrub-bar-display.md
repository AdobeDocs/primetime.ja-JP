---
description: TVSDKは、スライディングウィンドウプレイリストのストリームである特定の位置（時間）のシークを、ビデオオンデマンド(VOD)とライブストリームの両方でサポートしています。
seo-description: TVSDKは、スライディングウィンドウプレイリストのストリームである特定の位置（時間）のシークを、ビデオオンデマンド(VOD)とライブストリームの両方でサポートしています。
seo-title: シークスクラブバーに現在の再生位置を表示
title: シークスクラブバーに現在の再生位置を表示
uuid: a9f4dd6c-78cf-455c-8c31-b2f7b740d84a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# シークスクラブバーに現在の再生位置{#display-a-seek-scrub-bar-with-the-current-playback-position}を表示

TVSDKは、スライディングウィンドウプレイリストのストリームである特定の位置（時間）のシークを、ビデオオンデマンド(VOD)とライブストリームの両方でサポートしています。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVRでのみ可能です。

1. シーク用のコールバックを設定します。

       シークは非同期的なので、TVSDKは以下のシーク関連イベントをディスパッチします。
   
   * `QOSEventListener.onSeekStart`  — シーク開始。
   * `QOSEventListener.onSeekComplete`  — シークに成功しました。
   * `QOSEventListener.onOperationFailed`  — シークに失敗しました。

1. プレイヤーがシーク可能な状態になるのを待ちます。

   有効な状態は、PREPARED、COMPLETE、PAUSEDおよびPLAYINGです。

1. ネイティブのSeekBarを使用して`OnSeekBarChangeListener`を設定し、ユーザーがスクラブしている時間を確認します。
1. `QOSEventListener.onOperationFailed`をリッスンし、適切な処置を取ります。

   このイベントは、適切な警告を渡します。 アプリケーションは、例えば、シークを再試行するか、前の位置から再生を続行することで、どのように進むかを決定します。

1. TVSDKが`QOSEventListener.onSeekComplete`コールバックを呼び出すまで待ちます。
1. コールバックの位置パラメーターを使用して、最後に調整された再生位置を取得します。

   シーク後の実際の開始位置が、要求された位置と異なる場合があるので、これは重要です。 広告の時間の途中でシークや他の位置変更が行われたり、広告をスキップしたりすると、再生動作に影響する場合があります。

1. シークスクラブバーを表示する場合は、位置情報を使用します。

<!--<a id="example_9657AA855B6A4355B0E7D854596FFB54"></a>-->

**シークの例**

この例では、ユーザーはシークバーを使用して目的の位置にシークします。

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

