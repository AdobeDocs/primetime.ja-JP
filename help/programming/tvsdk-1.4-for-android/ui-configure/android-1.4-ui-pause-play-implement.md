---
description: TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。
title: ビデオの再生と一時停止
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# ビデオの再生と一時停止{#play-and-pause-a-video}

TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。

1. 以下を実行する一時停止/再生ボタンを作成します。
   1. プレイヤーがPREPARED状態以上になるのを待ちます。
   1. 開始を再生するには、TVSDKのplayメソッドを呼び出します。

      ```java
      void play() throws IllegalStateException;
      ```

   1. 再生を一時停止するには、TVSDKのpauseメソッドを呼び出します。

      ```java
      void pause() throws IllegalStateException;
      ```

1. `MediaPlayer.PlaybackEventListener.onStateChanged`コールバックを使用して、エラーを確認したり、他の適切なアクションを実行したりします。

   TVSDKは、pauseメソッドまたはplayメソッドが呼び出されると、このコールバックを呼び出します。 TVSDKは、PAUSEDやPLAYINGなどの新しい状態に関する情報を、コールバックで渡します。

