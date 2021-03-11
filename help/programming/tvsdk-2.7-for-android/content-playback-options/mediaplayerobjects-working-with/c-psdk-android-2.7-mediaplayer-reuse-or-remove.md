---
description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
title: MediaPlayerインスタンスの再利用または削除
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# MediaPlayerインスタンス{#reuse-or-remove-a-mediaplayer-instance}の再利用または削除

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

## MediaPlayerインスタンス{#section_E6A2446A2D0B4ACD9EA980685B2E57D9}のリセットまたは再利用

`MediaPlayer`インスタンスをリセットすると、`MediaPlayerStatus`で定義されているとおり、初期化されていないIDLEステータスに戻されます

* `MediaPlayer`インスタンスを再利用したいが、新しい`MediaResource`（ビデオコンテンツ）を読み込んで、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、`MediaPlayer`の再作成、リソースの再割り当てを行わなくても、`MediaPlayer`インスタンスを再利用できます。

* `MediaPlayer`がERROR状態で、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >これは、ERRORステータスから回復する唯一の方法です。

   1. `reset`を呼び出して、`MediaPlayer`インスタンスを初期化されていない状態に戻します。

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. `MediaPlayer.replaceCurrentResource()`を使用して別の`MediaResource`を読み込みます。

      >[!NOTE]
      >
      >エラーをクリアするには、同じ`MediaResource`を読み込みます。

   1. `STATUS_CHANGED`イベントコールバックを`PREPARED`ステータスで受け取ったら、再生を開始します。

## MediaPlayerインスタンスとリソース{#section_13A0914AFF784943ABC343F7EB249C4E}の解放

`MediaResource`が不要になった場合は、`MediaPlayer`インスタンスとリソースを解放する必要があります。

`MediaPlayer`オブジェクトを解放すると、この`MediaPlayer`オブジェクトに関連付けられている基になるハードウェアリソースは割り当て解除されます。

以下に、`MediaPlayer`をリリースする理由を示します。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な`MediaPlayer`オブジェクトをインスタンス化したままにすると、モバイルデバイスのバッテリ消費が継続的に発生する可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

* `MediaPlayer`を解放します。

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >`MediaPlayer`インスタンスを解放すると、そのインスタンスは使用できなくなります。 `MediaPlayer`インターフェイスのメソッドが解放された後に呼び出されると、`MediaPlayerException`がスローされます。