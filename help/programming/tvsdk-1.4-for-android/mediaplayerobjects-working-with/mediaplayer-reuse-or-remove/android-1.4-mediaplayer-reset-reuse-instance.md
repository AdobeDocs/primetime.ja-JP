---
description: MediaPlayer インスタンスをリセットすると、 MediaPlayerState で定義されている、初期化されていない IDLE 状態に戻されます。
title: MediaPlayer インスタンスのリセットまたは再利用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# MediaPlayer インスタンスのリセット、再利用、削除 {#reset-or-reuse-a-mediaplayer-instance}

不要になった MediaPlayer インスタンスをリセット、再利用、またはリリースできます。

MediaPlayer インスタンスをリセットすると、 MediaPlayerState で定義されている、初期化されていない IDLE 状態に戻されます。

この操作は、次の場合に役立ちます。

* 次の項目を再利用します： `MediaPlayer` インスタンスを使用するが、新しい `MediaResource` （ビデオコンテンツ）をクリックし、前のインスタンスを置き換えます。

  リセットを使用すると、 `MediaPlayer` リソースを解放するオーバーヘッドがなく、 `MediaPlayer`、およびリソースの再割り当て。

* 次の場合に `MediaPlayer` は ERROR 状態であり、クリアする必要があります。

  >[!IMPORTANT]
  >
  >これは、ERROR 状態から回復する唯一の方法です。

1. 通話 `reset` 返す `MediaPlayer` インスタンスを初期化されていない状態に変更します。

   ```java
   void reset() throws IllegalStateException; 
   ```

1. 用途 `MediaPlayer.replaceCurrentResource` 別の物を積み込む `MediaResource`.

   >[!TIP]
   >
   >エラーをクリアするには、同じ `MediaResource`.

1. 次を受け取ったとき： `STATUS_CHANGED` イベントコールバックが PREPARED ステータスになったら、再生を開始します。

## MediaPlayer インスタンスとリソースの解放{#release-a-mediaplayer-instance-and-resources}

MediaResource が不要になったら、MediaPlayer インスタンスとリソースを解放する必要があります。

をリリースする際に、 `MediaPlayer` オブジェクト、このオブジェクトに関連付けられている基になるハードウェアリソース `MediaPlayer` オブジェクトの割り当てが解除されます。

MediaPlayer をリリースする理由を次に示します。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な `MediaPlayer` オブジェクトは、モバイルデバイスのバッテリ消費を継続的に引き起こす可能性があります。
* 1 つのデバイスで同じビデオコーデックの複数のインスタンスがサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

1. をリリースします。 `MediaPlayer`.

   ```java
   void release() throws IllegalStateException;
   ```

次の期間の後に `MediaPlayer` インスタンスがリリースされているので、使用できなくなっています。 いずれかの方法で `MediaPlayer` インターフェイスは、リリース後に呼び出されます。 `IllegalStateException` がスローされます。
