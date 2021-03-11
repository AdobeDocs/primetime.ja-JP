---
description: MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。
title: MediaPlayerインスタンスとリソースの解放
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---


# MediaPlayerインスタンスとリソースの解放{#release-a-mediaplayer-instance-and-resources}

MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。

`MediaPlayer`オブジェクトを解放すると、この`MediaPlayer`オブジェクトに関連付けられている基になるハードウェアリソースは割り当て解除されます。

以下に、`MediaPlayer`をリリースする理由を示します。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

1. `MediaPlayer`を解放します。

   ```
   function release():void;
   ```

`MediaPlayer`インスタンスを解放すると、そのインスタンスは使用できなくなります。 `MediaPlayer`インターフェイスのメソッドが解放された後に呼び出されると、`IllegalStateException`がスローされます。