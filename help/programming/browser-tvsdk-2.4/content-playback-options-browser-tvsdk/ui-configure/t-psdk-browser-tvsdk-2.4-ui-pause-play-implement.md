---
description: 一時停止ボタンと再生ボタンに Browser TVSDK の動作を追加できます。
title: ビデオの再生と一時停止
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# ビデオの再生と一時停止{#play-and-pause-a-video}

一時停止ボタンと再生ボタンに Browser TVSDK の動作を追加できます。

1. 以下を実行する一時停止/再生ボタンを作成します。
   1. プレーヤーが PREPARED 状態以上になるのを待ちます。
   1. 再生を開始するには、 Browser TVSDK play メソッドを呼び出します。

      ```js
      play() → {AdobePSDK.PSDKErrorCode.SUCCESS}
      ```

   1. 再生を一時停止するには、 Browser TVSDK pause メソッドを呼び出します。

      ```java
      void pause() throws IllegalStateException;
      ```

1. をリッスンします。 `AdobePSDK.MediaPlayerStatusChangeEvent` イベントを使用して、エラーを確認したり、その他の適切なアクションを実行したりできます。

   Browser TVSDK は、pause または play メソッドが呼び出され、イベントオブジェクトに関する情報（新しい状態など）を渡すときに、このイベントをトリガーします。 `MediaPlayerStatus.PLAYING` または `MediaPlayerStatus.PAUSED`.
