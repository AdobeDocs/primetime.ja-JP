---
description: 一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。
seo-description: 一時停止ボタンと再生ボタンを追加して、ビデオを一時停止または再生できます。
seo-title: ビデオの再生と一時停止
title: ビデオの再生と一時停止
uuid: 66fefead-7f1d-46ed-a23e-381f25697978
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '123'
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

