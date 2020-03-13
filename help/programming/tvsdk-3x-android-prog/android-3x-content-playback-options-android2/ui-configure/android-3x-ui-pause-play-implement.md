---
description: 一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。
seo-description: 一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。
seo-title: ビデオの再生と一時停止
title: ビデオの再生と一時停止
uuid: 3778a1fb-929c-4579-a14c-561179473dea
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# ビデオの再生と一時停止 {#play-and-pause-a-video}

一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。

1. 一時停止または再生ボタンを作成するには：
   1. プレイヤーが準備された状態になるまで待ちます。
   1. 再生を開始するには、次のメソッドを呼び `play` 出します。

      ```java
      void play() throws MediaPlayerException;
      ```

   1. 再生を一時停止するには、次のメソッドを呼び `pause()` 出します。

      ```java
      void pause() throws MediaPlayerException;
      ```

1. ステータスが変更されたイベントコールバックを使用して、エラーを確認したり、他の適切なアクションを実行したりします。

   TVSDKは、このコールバックをORに対 `pause()` して呼び `play()` 出し、一時停止や再生などの新しいステータスの変更を含む、ステータス変更に関する情報を渡します。