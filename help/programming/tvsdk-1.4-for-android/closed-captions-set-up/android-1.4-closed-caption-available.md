---
description: クローズドキャプションは、サウンドが聞こえない場合、またはビューアが耳に不自由な場合に、ビデオのオーディオ部分をテキストとして画面に表示します。
seo-description: クローズドキャプションは、サウンドが聞こえない場合、またはビューアが耳に不自由な場合に、ビデオのオーディオ部分をテキストとして画面に表示します。
seo-title: 使用可能なトラックの中から現在のキャプショントラックを選択
title: 使用可能なトラックの中から現在のキャプショントラックを選択
uuid: 637a70c9-9bef-4b13-8b1f-62f22f983e80
translation-type: tm+mt
source-git-commit: 53924aa8ba90555d58d15ee10fb14221c7dffaff
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---


# 使用可能なトラックの中から現在のキャプショントラックを選択{#select-a-current-caption-track-from-among-available-tracks}

現在使用可能なクローズドキャプショントラックのリストからトラックを選択できます。 これが現在のトラックになり、表示がオンの場合に表示されます。 一部のトラックは最初は使用できない場合があるので、使用可能になったことを示すイベントをリッスンします。

>[!TIP]
>
>クローズドキャプションは常に有効です。 デフォルトのクローズドキャプショントラックはすべて存在すると見なされます。 デフォルトのトラック（CC1-CC4、CS1-CS6など）は、に列挙され `ClosedCaptionsTrack.DefaultCCTypes`ます。 再生が始まると、TVSDKは、これらのチャネルのいずれかに関するアクティビティを探します。 アクティビティが見つかった場合は、そのトラックの `isActive` メソッドを設定し、 `MediaPlayer.PlaybackEventListener.onUpdated` イベントをディスパッチします。

1. メディアプレイヤーがPREPARED状態になるまで待ちます。
1. 以下のイベントをリッスンします。

   * `MediaPlayer.PlaybackEventListener.onStateChanged with state MediaPlayer.PlayerState.INITIALIZED`:クローズドキャプショントラックの初期リストを使用できます

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
           mediaPlayer.getCurrentItem().selectClosedCaptionsTrack(track); 
           selectedClosedCaptionsIndex = i; 
       } 
   }
   ```

1. 使用可能なトラックが増えたことを示すイベントのリスナーを実装します。 TVSDKがイベントをディスパッチする場合、使用可能なトラックの現在のリストを取得します。

   イベントが発生するたびにリストを取得し、常に最新のリストを持つようにします。
