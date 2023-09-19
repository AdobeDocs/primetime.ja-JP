---
description: MediaPlayer ビューを使用してビデオを再生した後は、 TVSDK メソッドを使用するか、手動で非表示にして再度表示することができます。
title: ビデオビューを非表示にする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# ビデオビューを非表示にする{#hide-a-video-view}

MediaPlayer ビューを使用してビデオを再生した後は、 TVSDK メソッドを使用するか、手動で非表示にして再度表示することができます。

ビデオを一時停止してから、ディスプレイからクリアまたは移動する必要があります。
* オプション 1：でビデオフレームをクリアします。 `MediaPlayer.clearVideo`後でフ&#x200B;レームを置き換えます。
   * 非表示にするビデオを一時停止します。
   * を呼び出して、表示されているビデオフレームを削除します。 `MediaPlayer.clearVideo`.
   * をリセットするには、以下を実行します。 `MediaPlayer` 再び再生できるように、を呼び出します。 `replaceCurrentResource` または `replaceCurrentItem`.
* オプション 2: `MediaPlayer` 画面を表示し、置き換える必要なく後で戻します。
   * 非表示にするビデオを一時停止します。
   * ビューをステージ外に移動します。 例：

     ```
     view.x = -300; 
     view.y = -300;
     ```

   * ビデオを再度表示するには、ビューをステージに戻します。
