---
description: MediaPlayerインスタンスをリセットすると、MediaPlayerStatusで定義されている、初期化されていないIDLE状態に戻されます。
seo-description: MediaPlayerインスタンスをリセットすると、MediaPlayerStatusで定義されている、初期化されていないIDLE状態に戻されます。
seo-title: MediaPlayerインスタンスのリセットまたは再利用
title: MediaPlayerインスタンスのリセットまたは再利用
uuid: b376096b-0aed-4ac2-96e5-e30a4eaf742e
translation-type: tm+mt
source-git-commit: c547002eb8946f8ccc5a79d0836f3f814e823b97

---


# MediaPlayerインスタンスのリセットまたは再利用{#reset-or-reuse-a-mediaplayer-instance}

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

MediaPlayerインスタンスをリセットすると、MediaPlayerStatusで定義されている、初期化されていないIDLE状態に戻されます。

この操作は、次の場合に役立ちます。

* インスタンスを再利用したいが、 `MediaPlayer` 新しい（ビデオコンテンツ）を読み込ん `MediaResource` で、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、再 `MediaPlayer` 作成およびリソースの再割り当てを行うオーバーヘッドなしで、インスタ `MediaPlayer`ンスを再利用できます。 メソッ `replaceCurrentItem` ドとメ `replaceCurrentResource` ソッドは、リセットメソッドを呼び出すことなく、これらの手順を自動的に実行します。

* がERRORステー `MediaPlayer` タスで、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >これは、ERRORステータスから回復する唯一の方法です。

1. インスタ `reset` ンスを初期化されて `MediaPlayer` いない状態に戻すための呼び出し：

   ```
   function reset():void; 
   ```

1. またはを使 `MediaPlayer.replaceCurrentItem` 用して、 `MediaPlayer.replaceCurrentResource` 別のを読み込みま `MediaResource`す。

   >[!TIP]
   >
   >エラーをクリアするには、同じエラーを読み込みま `MediaResource`す。

1. ステータスのが表示され `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` たら、 `PREPARED` 再生を開始します。
