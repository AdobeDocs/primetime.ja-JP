---
description: TVSDK の動作を追加して、一時停止ボタンと再生ボタンを追加できます。
title: ビデオの再生と一時停止
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# ビデオの再生と一時停止{#play-and-pause-a-video}

TVSDK の動作を追加して、一時停止ボタンと再生ボタンを追加できます。

1. 以下を実行する一時停止/再生ボタンを作成します。
   1. プレーヤーが PREPARED 状態以上になるのを待ちます。
   1. 再生を開始するには、 TVSDK play メソッドを呼び出します。

      ```java
      void play() throws IllegalStateException;
      ```

   1. 再生を一時停止するには、 TVSDK の pause メソッドを呼び出します。

      ```java
      void pause() throws IllegalStateException;
      ```

1. 以下を使用します。 `MediaPlayer.PlaybackEventListener.onStateChanged` エラーを確認するか、その他の適切なアクションを実行するコールバック。

   TVSDK は、 pause または play メソッドが呼び出されると、このコールバックを呼び出します。 TVSDK は、PAUSED や PLAYING などの新しい状態を含む、コールバックの状態変更に関する情報を渡します。
