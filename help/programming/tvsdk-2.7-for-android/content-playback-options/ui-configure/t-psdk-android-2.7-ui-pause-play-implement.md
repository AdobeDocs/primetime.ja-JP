---
description: 一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。
title: ビデオの再生と一時停止
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# ビデオの再生と一時停止{#play-and-pause-a-video}

一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。

1. 一時停止または再生ボタンを作成するには：
   1. プレイヤーが準備済み状態になるまで待ちます。
   1. 開始を再生するには、`play`メソッドを呼び出します。

      ```java
      void play() throws MediaPlayerException;
      ```

   1. 再生を一時停止するには、`pause()`メソッドを呼び出します。

      ```java
      void pause() throws MediaPlayerException;
      ```

1. ステータス変更イベントコールバックを使用して、エラーを確認したり、他の適切なアクションを実行したりします。

   TVSDKは、このコールバックを`pause()`または`play()`に対して呼び出し、一時停止や再生などの新しいステータス変更など、ステータス変更に関する情報を渡します。

