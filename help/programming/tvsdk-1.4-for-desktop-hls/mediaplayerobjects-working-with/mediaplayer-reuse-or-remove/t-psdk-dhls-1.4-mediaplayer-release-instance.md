---
description: MediaResource が不要になったら、MediaPlayer インスタンスとリソースを解放する必要があります。
title: MediaPlayer インスタンスとリソースの解放
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# MediaPlayer インスタンスとリソースの解放{#release-a-mediaplayer-instance-and-resources}

MediaResource が不要になったら、MediaPlayer インスタンスとリソースを解放する必要があります。

をリリースする際に、 `MediaPlayer` オブジェクト、このオブジェクトに関連付けられている基になるハードウェアリソース `MediaPlayer` オブジェクトの割り当てが解除されます。

以下は、 `MediaPlayer`:

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 1 つのデバイスで同じビデオコーデックの複数のインスタンスがサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

1. をリリースします。 `MediaPlayer`.

   ```
   function release():void;
   ```

次の期間の後に `MediaPlayer` インスタンスがリリースされているので、使用できなくなっています。 いずれかの方法で `MediaPlayer` インターフェイスは、リリース後に呼び出されます。 `IllegalStateException` がスローされます。
