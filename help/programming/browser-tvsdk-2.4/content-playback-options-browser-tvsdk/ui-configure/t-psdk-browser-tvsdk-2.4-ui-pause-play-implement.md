---
description: 一時停止ボタンと再生ボタンに、ブラウザーTVSDKの動作を追加できます。
title: ビデオの再生と一時停止
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# ビデオの再生と一時停止{#play-and-pause-a-video}

一時停止ボタンと再生ボタンに、ブラウザーTVSDKの動作を追加できます。

1. 以下を実行する一時停止/再生ボタンを作成します。
   1. プレイヤーがPREPARED状態以上になるのを待ちます。
   1. 開始を再生するには、Browser TVSDK playメソッドを呼び出します。

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. 再生を一時停止するには、ブラウザーTVSDKの一時停止メソッドを呼び出します。

      ```java
      void pause() throws IllegalStateException;
      ```

1. `AdobePSDK.MediaPlayerStatusChangeEvent`イベントをリッスンして、エラーを確認したり、その他の適切な処置を取ったりします。

   ブラウザーTVSDKは、pauseまたはplayメソッドが呼び出されるとこのイベントをトリガーし、`MediaPlayerStatus.PLAYING`や`MediaPlayerStatus.PAUSED`などの新しい状態を含むイベントオブジェクトに関する情報を渡します。

