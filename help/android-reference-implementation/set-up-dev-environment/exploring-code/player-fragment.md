---
description: PlayerFragmentクラスは、完全に有効な機能マネージャーを作成するためにコードを編集する場所です。
seo-description: PlayerFragmentクラスは、完全に有効な機能マネージャーを作成するためにコードを編集する場所です。
seo-title: PlayerFragment
title: PlayerFragment
uuid: 83f02c31-f3b1-4d16-97c8-5b391e8c999a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# PlayerFragment {#playerfragment}

PlayerFragmentクラスは、完全に有効な機能マネージャーを作成するためにコードを編集する場所です。

このク `PlayerFragment` ラスには、、、、などのすべてのUIコンポ `playerFrame`ーネント `ControlBar`が含ま `playerClickableAdFragment`れていま `adOverlay`す。

これらすべてのコンポーネントの初期化、プレイヤーの作成、ビューの設定、メディアプレイヤーの機能マネージャーの作成、再開、再生、一時停止などのメディアイベントの処理、イベントリスナーの処理、 `QoSManager`、、 `DRMManager`、 `CCManager`、 `AAManager``AdsManager`、 `PlaybackManager`、 `EntitlementManager`、、

ISの設定パラメーターを含むXMLファ `PlayerFragment` イル `res/layout/fragment_player.xml`。

機能マネージャを作成する前に、次のコードがファイル内にあることを確認して、メディアプレイヤを作成する必要があ `PlayerFragment.java` ります。

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
