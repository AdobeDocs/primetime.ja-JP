---
description: PlayerFragment クラスでは、コードを編集して、完全に有効な機能マネージャーを作成できます。
title: PlayerFragment
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# PlayerFragment {#playerfragment}

PlayerFragment クラスでは、コードを編集して、完全に有効な機能マネージャーを作成できます。

The `PlayerFragment` クラスには、すべての UI コンポーネント ( `playerFrame`, `ControlBar`, `playerClickableAdFragment`、および `adOverlay`.

これは、これらのすべてのコンポーネントの初期化と、プレーヤーの作成、ビューの設定、メディアプレーヤーの機能マネージャーの作成、再開、再生、一時停止などのメディアイベントの処理、 `QoSManager`, `DRMManager`, `CCManager`, `AAManager`, `AdsManager`, `PlaybackManager`、および `EntitlementManager`.

の設定パラメーターを含む XML ファイル `PlayerFragment` 次に該当 `res/layout/fragment_player.xml`.

機能マネージャを作成する前に、次のコードが `PlayerFragment.java` ファイル：

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
