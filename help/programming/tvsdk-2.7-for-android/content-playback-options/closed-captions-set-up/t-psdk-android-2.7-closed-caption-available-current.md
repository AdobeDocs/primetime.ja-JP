---
description: 現在使用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これが現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない場合があるので、使用可能になったことを示すイベントをリッスンします。
title: 使用可能なトラックの中から現在のキャプショントラックを選択
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

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