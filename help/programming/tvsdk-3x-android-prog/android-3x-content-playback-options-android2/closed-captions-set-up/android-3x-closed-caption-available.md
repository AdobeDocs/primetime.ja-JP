---
description: 現在利用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これは現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない可能性があるので、使用可能になったトラックが増えたことを示すイベントをリッスンします。
title: 利用可能なトラックの中から現在のキャプショントラックを選択
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 利用可能なトラックの中から現在のキャプショントラックを選択 {#select-a-current-caption-track-from-among-available-tracks}

現在利用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これは現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない可能性があるので、使用可能になったトラックが増えたことを示すイベントをリッスンします。

1. メディアプレーヤーが少なくとも `PREPARED` ステータス。
1. 次のイベントをリッスンします。

   * `MediaPlayerEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.INITIALIZED`：クローズドキャプショントラックの初期リストが使用可能です。

1. 現在使用可能なクローズドキャプショントラックのリストを取得します。

   例：

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. 現在のトラックとなる使用可能なトラックを選択します。

   例：

   ```java
   // Select the initial CC track. 
   for (int i = 0; i < ccTracks.size(); i++) { 
       ClosedCaptionsTrack track = ccTracks.get(i); 
       if (track.getName().equals(INITIAL_CC_TRACK)) {
        <b>mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track);</b> 
             selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. 使用可能なトラックが増えたことを示すイベントのリスナーを実装します。 TVSDK がイベントをディスパッチする際に、使用可能なトラックの現在のリストを取得します。

   イベントが発生するたびにリストを取得し、常に最新のリストが表示されるようにします。
