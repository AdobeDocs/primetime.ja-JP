---
description: クローズドキャプションは、サウンドが聞こえない場合や、ビューアが聞き取りにくい場合に、ビデオのオーディオ部分をテキストとして画面に表示します。
seo-description: クローズドキャプションは、サウンドが聞こえない場合や、ビューアが聞き取りにくい場合に、ビデオのオーディオ部分をテキストとして画面に表示します。
seo-title: 使用可能なトラックの中から現在のキャプショントラックを選択
title: 使用可能なトラックの中から現在のキャプショントラックを選択
uuid: 637a70c9-9bef-4b13-8b1f-62f22f983e80
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 使用可能なトラックの中から現在のキャプショントラックを選択{#select-a-current-caption-track-from-among-available-tracks}

現在使用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これが現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない場合があるので、より多くのトラックが使用可能になったことを示すイベントをリッスンします。

>[!TIP]
>
>クローズドキャプションは常に有効です。 すべてのデフォルトのクローズドキャプショントラックが存在すると見なされます。 デフォルトのトラック（CC1 ～ CC4、CS1 ～ CS6など）は、に列挙されます `ClosedCaptionsTrack.DefaultCCTypes`。 再生が始まると、TVSDKはこれらのチャネルのいずれかでのアクティビティを探します。 アクティビティが見つかった場合、そのトラッ `isActive` クのメソッドを設定し、イベントをディスパッチ `MediaPlayer.PlaybackEventListener.onUpdated` します。

1. メディアプレイヤーがPREPARED状態になるまで待ちます。
1. 以下のイベントをリッスンします。

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`:クローズドキャプショントラックの初期リストを使用できます

1. 現在使用可能なすべてのクローズドキャプショントラックのリストを取得します。

   例：

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
         mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. 現在のトラックにする利用可能なトラックを選択します。

   例：

   ```java
   // Select the initial CC track. 
   for (int i = 0; i < ccTracks.size(); i++) { 
       ClosedCaptionsTrack track = ccTracks.get(i); 
       if (track.getName().equals(INITIAL_CC_TRACK)) { 
   
<b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b>selectedClosedCaptionsIndex = i;}}

```
1. Implement a listener for the event that indicates that more tracks are available. When TVSDK dispatches the event, retrieve the current list of available tracks.

Retrieve the list each time that the event occurs to ensure that you always have the most current list.

