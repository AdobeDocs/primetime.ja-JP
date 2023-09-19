---
description: 一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。
title: ビデオの再生と一時停止
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# ビデオの再生と一時停止 {#play-and-pause-a-video}

一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。

1. 一時停止または再生ボタンを作成するには：
   1. プレーヤーが準備済み状態以上になるのを待ちます。
   1. 再生を開始するには、 `play` メソッド：

      ```java
      void play() throws MediaPlayerException;
      ```

   1. 再生を一時停止するには、 `pause()` メソッド：

      ```java
      void pause() throws MediaPlayerException;
      ```

1. status changed イベントコールバックを使用して、エラーを確認したり、他の適切なアクションを実行したりします。

   TVSDK は、このコールバックを `pause()` または `play()` およびは、一時停止や再生などの新しいステータスの変更に関する情報を渡します。
