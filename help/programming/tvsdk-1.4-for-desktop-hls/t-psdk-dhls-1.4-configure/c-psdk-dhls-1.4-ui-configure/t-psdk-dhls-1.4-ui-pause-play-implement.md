---
description: TVSDK の動作を追加して、一時停止ボタンと再生ボタンを追加できます。
title: ビデオの再生と一時停止
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# ビデオの再生と一時停止{#play-and-pause-a-video}

TVSDK の動作を追加して、一時停止ボタンと再生ボタンを追加できます。

1. 以下を実行する一時停止/再生ボタンを作成します。
   1. プレーヤーが PREPARED ステータス以上になるのを待ちます。
   1. 再生を開始するには、 TVSDK play メソッドを呼び出します。

      ```
      function play():void;
      ```

   1. 再生を一時停止するには、 TVSDK の pause メソッドを呼び出します。

      ```
      function pause():void;
      ```

1. コールバックを使用して `MediaPlayerStatusChangeEvent.STATUS_CHANGED` イベントを使用して、エラーを確認したり、その他の適切なアクションを実行したりできます。

   TVSDK は、 pause または play メソッドが呼び出されると、このコールバックを呼び出します。 TVSDK は、PAUSED や PLAYING などの新しいステータスの変更に関する情報をコールバックに渡します。
