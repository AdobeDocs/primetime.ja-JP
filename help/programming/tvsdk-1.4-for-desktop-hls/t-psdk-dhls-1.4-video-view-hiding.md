---
description: MediaPlayer表示を使用してビデオを再生した後、TVSDKメソッドを使用するか、手動で非表示にして再び表示することができます。
title: ビデオ表示の非表示
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---


# ビデオ表示を非表示{#hide-a-video-view}

MediaPlayer表示を使用してビデオを再生した後、TVSDKメソッドを使用するか、手動で非表示にして再び表示することができます。

ビデオをディスプレイからクリアまたは移動する前に、一時停止する必要があります。
* オプション1:`MediaPlayer.clearVideo`でビデオフレームをクリアし、後でフレームを置き換え&#x200B;ます。
   * 非表示にするビデオを一時停止します。
   * `MediaPlayer.clearVideo`を呼び出して、表示されているビデオフレームを削除します。
   * `MediaPlayer`を再生できるようにリセットするには、`replaceCurrentResource`または`replaceCurrentItem`を呼び出します。
* オプション2:`MediaPlayer`表示を画面外に移動し、置き換えることなく後で元に戻します。
   * 非表示にするビデオを一時停止します。
   * 表示をステージ外に移動します。 例：

      ```
      view.x = -300; 
      view.y = -300;
      ```

   * ビデオを再び表示するには、表示をステージに戻します。
