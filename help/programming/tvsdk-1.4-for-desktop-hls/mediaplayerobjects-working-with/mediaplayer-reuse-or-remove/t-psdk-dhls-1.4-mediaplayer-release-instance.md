---
description: MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。
seo-description: MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。
seo-title: MediaPlayerインスタンスとリソースの解放
title: MediaPlayerインスタンスとリソースの解放
uuid: e7b2112e-8add-4789-9345-5f829d39d639
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# MediaPlayerインスタンスとリソースの解放{#release-a-mediaplayer-instance-and-resources}

MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。

オブジェクトを解放す `MediaPlayer` ると、このオブジェクトに関連付けられている基になるハードウェアリソ `MediaPlayer` ースの割り当てが解除されます。

以下に、をリリースする理由を示しま `MediaPlayer`す。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

1. を解放しま `MediaPlayer`す。

   ```
   function release():void;
   ```

インスタンス `MediaPlayer` を解放した後は、使用できなくなります。 インターフェイスのメソッド `MediaPlayer` が解放された後に呼び出された場合、がスロ `IllegalStateException` ーされます。