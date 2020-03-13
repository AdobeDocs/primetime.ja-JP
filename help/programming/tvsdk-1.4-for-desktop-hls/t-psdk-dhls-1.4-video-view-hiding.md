---
description: ビデオの再生にMediaPlayerビューを使用した後、TVSDKメソッドを使用するか、手動で非表示にし、再び表示することができます。
seo-description: ビデオの再生にMediaPlayerビューを使用した後、TVSDKメソッドを使用するか、手動で非表示にし、再び表示することができます。
seo-title: ビデオビューの非表示
title: ビデオビューの非表示
uuid: 7cc02bf4-41ee-4af0-98ba-df070b50b88d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ビデオビューの非表示{#hide-a-video-view}

ビデオの再生にMediaPlayerビューを使用した後、TVSDKメソッドを使用するか、手動で非表示にし、再び表示することができます。

ビデオをクリアまたはディスプレイから移動する前に、ビデオを一時停止する必要があります。
* オプション1:ビデオフレームを消去し、後でフ&#x200B;レームを置き換えます。 `MediaPlayer.clearVideo`
   * 非表示にするビデオを一時停止します。
   * を呼び出して、表示されたビデオフレームを削除しま `MediaPlayer.clearVideo`す。
   * 再び再生できるよ `MediaPlayer` うにリセットするには、またはを呼び出 `replaceCurrentResource` しま `replaceCurrentItem`す。
* オプション2:ビューを画 `MediaPlayer` 面の外に移動し、後で置き換える必要なく戻します。
   * 非表示にするビデオを一時停止します。
   * ビューをステージの外に移動します。 例：

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * ビデオを再び表示するには、ビューをステージに戻します。
