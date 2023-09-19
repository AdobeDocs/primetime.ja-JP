---
description: クローズドキャプションは、サウンドが聞こえない場合やビューアが聞きにくい場合に、ビデオのオーディオ部分をテキストとして画面に表示します。
title: 利用可能なトラックの中から現在のキャプショントラックを選択
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# 利用可能なトラックの中から現在のキャプショントラックを選択{#select-a-current-caption-track-from-among-available-tracks}

現在利用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これは現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない可能性があるので、使用可能になったトラックが増えたことを示すイベントをリッスンします。

>[!TIP]
>
>クローズドキャプションは常に有効です。 デフォルトのクローズドキャプショントラックはすべて存在すると見なされます。 デフォルトのトラック (CC1-CC4、CS1-CS6 など ) は、 `ClosedCaptionsTrack.DefaultCCTypes`. 再生が開始されると、 TVSDK は、これらのチャネルのいずれかでアクティビティを探します。 アクティビティが見つかった場合は、 `isActive` メソッドを使用して、 `MediaPlayer.PlaybackEventListener.onUpdated` イベント。

1. メディアプレーヤーが PREPARED 状態以上になるのを待ちます。
1. 次のイベントをリッスンします。

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`：クローズドキャプショントラックの初期リストを使用できます

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
           mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track); 
           selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. 使用可能なトラックが増えたことを示すイベントのリスナーを実装します。 TVSDK がイベントをディスパッチする際に、使用可能なトラックの現在のリストを取得します。

   イベントが発生するたびにリストを取得し、常に最新のリストが表示されるようにします。
