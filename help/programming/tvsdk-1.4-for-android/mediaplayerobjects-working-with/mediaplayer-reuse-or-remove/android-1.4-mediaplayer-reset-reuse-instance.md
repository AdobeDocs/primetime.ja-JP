---
description: MediaPlayerインスタンスをリセットすると、MediaPlayerStateで定義されているとおり、初期化されていないIDLE状態に戻されます。
seo-description: MediaPlayerインスタンスをリセットすると、MediaPlayerStateで定義されているとおり、初期化されていないIDLE状態に戻されます。
seo-title: MediaPlayerインスタンスのリセットまたは再利用
title: MediaPlayerインスタンスのリセットまたは再利用
uuid: 72cc4511-8ab0-44e5-b93c-b36f0321bba8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# MediaPlayerインスタンス{#reset-or-reuse-a-mediaplayer-instance}のリセット、再利用、削除

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

MediaPlayerインスタンスをリセットすると、MediaPlayerStateで定義されているとおり、初期化されていないIDLE状態に戻されます。

この操作は、次の場合に役立ちます。

* `MediaPlayer`インスタンスを再利用したいが、新しい`MediaResource`（ビデオコンテンツ）を読み込んで、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、`MediaPlayer`の再作成、リソースの再割り当てを行わなくても、`MediaPlayer`インスタンスを再利用できます。

* `MediaPlayer`がERROR状態で、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >ERROR状態から回復するには、この方法しかありません。

1. `reset`を呼び出して、`MediaPlayer`インスタンスを初期化されていない状態に戻します。

   ```java
   void reset() throws IllegalStateException; 
   ```

1. `MediaPlayer.replaceCurrentResource`を使用して別の`MediaResource`を読み込みます。

   >[!TIP]
   >
   >エラーをクリアするには、同じ`MediaResource`を読み込みます。

1. PREPAREDステータスで`STATUS_CHANGED`イベントコールバックを受け取ったら、再生を開始します。

## MediaPlayerインスタンスとリソースの解放{#release-a-mediaplayer-instance-and-resources}

MediaResourceが不要になった場合は、MediaPlayerインスタンスとリソースを解放する必要があります。

`MediaPlayer`オブジェクトを解放すると、この`MediaPlayer`オブジェクトに関連付けられている基になるハードウェアリソースは割り当て解除されます。

MediaPlayerをリリースする理由は次のとおりです。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な`MediaPlayer`オブジェクトを残すと、モバイルデバイスのバッテリ消費が継続的に発生する可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

1. `MediaPlayer`を解放します。

   ```java
   void release() throws IllegalStateException;
   ```

`MediaPlayer`インスタンスを解放すると、そのインスタンスは使用できなくなります。 `MediaPlayer`インターフェイスのメソッドが解放された後に呼び出されると、`IllegalStateException`がスローされます。