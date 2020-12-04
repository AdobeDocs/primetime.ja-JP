---
description: 一時停止ボタンと再生ボタンに、ブラウザーTVSDKの動作を追加できます。
seo-description: 一時停止ボタンと再生ボタンに、ブラウザーTVSDKの動作を追加できます。
seo-title: ビデオの再生と一時停止
title: ビデオの再生と一時停止
uuid: 4053ea9e-6b74-41e9-ad04-087ad13e3698
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '127'
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

   ブラウザーTVSDKは、pauseまたはplayメソッドが呼び出され、`MediaPlayerStatus.PLAYING`や`MediaPlayerStatus.PAUSED`などの新しい状態を含むイベントオブジェクトに関する情報を渡すときに、このイベントをトリガーします。

