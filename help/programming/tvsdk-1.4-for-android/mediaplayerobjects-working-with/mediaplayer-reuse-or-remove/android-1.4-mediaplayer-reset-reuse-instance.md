---
description: MediaPlayerインスタンスをリセットすると、MediaPlayerStateで定義されている、初期化されていないIDLE状態に戻されます。
seo-description: MediaPlayerインスタンスをリセットすると、MediaPlayerStateで定義されている、初期化されていないIDLE状態に戻されます。
seo-title: MediaPlayerインスタンスのリセットまたは再利用
title: MediaPlayerインスタンスのリセットまたは再利用
uuid: 72cc4511-8ab0-44e5-b93c-b36f0321bba8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayerインスタンスのリセット、再利用または削除 {#reset-or-reuse-a-mediaplayer-instance}

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

MediaPlayerインスタンスをリセットすると、MediaPlayerStateで定義されている、初期化されていないIDLE状態に戻されます。

この操作は、次の場合に役立ちます。

* インスタンスを再利用したいが、 `MediaPlayer` 新しい（ビデオコンテンツ）を読み込ん `MediaResource` で、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、再 `MediaPlayer` 作成およびリソースの再割り当てを行うオーバーヘッドなしで、インスタ `MediaPlayer`ンスを再利用できます。

* がERROR状態 `MediaPlayer` で、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >これは、ERROR状態から回復する唯一の方法です。

1. インスタ `reset` ンスを初期化されて `MediaPlayer` いない状態に戻すための呼び出し：

   ```java
   void reset() throws IllegalStateException; 
   ```

1. を使用し `MediaPlayer.replaceCurrentResource` て、別のを読み込みま `MediaResource`す。

   >[!TIP]
   >
   >エラーをクリアするには、同じエラーを読み込みま `MediaResource`す。

1. PREPAREDステータスのイベントコ `STATUS_CHANGED` ールバックを受け取ったら、再生を開始します。

## MediaPlayerインスタンスとリソースの解放{#release-a-mediaplayer-instance-and-resources}

MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。

オブジェクトを解放す `MediaPlayer` ると、このオブジェクトに関連付けられている基になるハードウェアリソ `MediaPlayer` ースの割り当てが解除されます。

MediaPlayerをリリースする理由は、次のとおりです。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な物体を残す `MediaPlayer` と、モバイルデバイスのバッテリー消費が継続的に発生する可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

1. を解放しま `MediaPlayer`す。

   ```java
   void release() throws IllegalStateException;
   ```

インスタンス `MediaPlayer` を解放した後は、使用できなくなります。 インターフェイスのメソッド `MediaPlayer` が解放された後に呼び出された場合、がスロ `IllegalStateException` ーされます。