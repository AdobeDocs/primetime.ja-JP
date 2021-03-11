---
description: PlayerFragmentクラスでは、コードを編集して、完全に有効な機能マネージャーを作成できます。
title: PlayerFragment
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# PlayerFragment {#playerfragment}

PlayerFragmentクラスでは、コードを編集して、完全に有効な機能マネージャーを作成できます。

`PlayerFragment`クラスには、`playerFrame`、`ControlBar`、`playerClickableAdFragment`、`adOverlay`など、すべてのUIコンポーネントが含まれます。

これらのコンポーネントの初期化と、プレイヤーの作成、表示の設定、メディアプレイヤーの機能マネージャーの作成、再開、再生、一時停止などのメディアイベントの処理、`QoSManager`、`CCManager`、`AAManager`、`AdsManager`、`PlaybackManager`、`EntitlementManager`のイベントリスナーの処理を行います。`DRMManager`

`PlayerFragment`の設定パラメーターを含むXMLファイルは`res/layout/fragment_player.xml`です。

機能マネージャを作成する前に、`PlayerFragment.java`ファイル内に次のコードがあることを確認して、メディアプレイヤを作成する必要があります。

```java
private MediaPlayer createMediaPlayer() { 
  MediaPlayer mediaPlayer =  
    DefaultMediaPlayer.create(getActivity().getApplicationContext()); 
  return mediaPlayer; 
}
```
