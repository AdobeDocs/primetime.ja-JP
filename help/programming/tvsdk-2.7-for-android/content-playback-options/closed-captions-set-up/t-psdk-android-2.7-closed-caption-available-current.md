---
description: 現在使用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これが現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない場合があるので、使用可能になったことを示すイベントをリッスンします。
seo-description: 現在使用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これが現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない場合があるので、使用可能になったことを示すイベントをリッスンします。
seo-title: 使用可能なトラックの中から現在のキャプショントラックを選択
title: 使用可能なトラックの中から現在のキャプショントラックを選択
uuid: d582779a-2789-4e2a-85f6-1a0b9b847382
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---


# 使用可能なトラックの中から現在のキャプショントラックを選択{#select-a-current-caption-track-from-among-available-tracks}

現在使用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これが現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない場合があるので、使用可能になったことを示すイベントをリッスンします。

1. メディアプレイヤーが`PREPARED`以上のステータスになるのを待ちます。
1. 以下のイベントをリッスンします。

   * `MediaPlayerEvent.STATUS_CHANGED` ステータス `MediaPlayerStatus.INITIALIZED`:クローズドキャプショントラックの初期リストを使用できます。

1. 現在使用可能なクローズドキャプショントラックのリストを取得します。

   例：

   ```java
   List<ClosedCaptionsTrack> ccTracks = 
     mediaPlayer.getCurrentItem().getClosedCaptionsTracks();
   ```

1. 現在のトラックにする使用可能なトラックを選択します。

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

1. 使用可能なトラックが増えたことを示すイベントのリスナーを実装します。 TVSDKがイベントをディスパッチする場合、使用可能なトラックの現在のリストを取得します。

   イベントが発生するたびにリストを取得し、常に最新のリストを持つようにします。