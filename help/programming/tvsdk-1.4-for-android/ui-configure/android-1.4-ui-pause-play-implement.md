---
description: TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。
seo-description: TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。
seo-title: ビデオの再生と一時停止
title: ビデオの再生と一時停止
uuid: 24b26364-5cb8-4a95-9574-cc52ddfa876b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ビデオの再生と一時停止{#play-and-pause-a-video}

TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。

1. 次を実行する一時停止/再生ボタンを作成します。
   1. プレイヤーがPREPARED状態になるまで待ちます。
   1. 再生を開始するには、TVSDKのplayメソッドを呼び出します。

      ```java
      void play() throws IllegalStateException;
      ```

   1. 再生を一時停止するには、TVSDKのpauseメソッドを呼び出します。

      ```java
      void pause() throws IllegalStateException;
      ```

1. このコールバックを `MediaPlayer.PlaybackEventListener.onStateChanged` 使用して、エラーを確認したり、他の適切なアクションを実行したりします。

   TVSDKは、pauseまたはplayメソッドが呼び出されると、このコールバックを呼び出します。 TVSDKは、PAUSEDやPLAYINGなどの新しい状態を含む、状態変更に関する情報をコールバックに渡します。

