---
description: MediaPlayerインスタンスをリセットすると、MediaPlayerStatusで定義されているとおり、初期化されていないIDLE状態に戻されます。
seo-description: MediaPlayerインスタンスをリセットすると、MediaPlayerStatusで定義されているとおり、初期化されていないIDLE状態に戻されます。
seo-title: MediaPlayerインスタンスのリセットまたは再利用
title: MediaPlayerインスタンスのリセットまたは再利用
uuid: b376096b-0aed-4ac2-96e5-e30a4eaf742e
translation-type: tm+mt
source-git-commit: c547002eb8946f8ccc5a79d0836f3f814e823b97
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# MediaPlayerインスタンスのリセットまたは再利用{#reset-or-reuse-a-mediaplayer-instance}

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

MediaPlayerインスタンスをリセットすると、MediaPlayerStatusで定義されているとおり、初期化されていないIDLE状態に戻されます。

この操作は、次の場合に役立ちます。

* `MediaPlayer`インスタンスを再利用したいが、新しい`MediaResource`（ビデオコンテンツ）を読み込んで、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、`MediaPlayer`の再作成、リソースの再割り当てを行わなくても、`MediaPlayer`インスタンスを再利用できます。 これらの手順は、`replaceCurrentItem`メソッドと`replaceCurrentResource`メソッドが自動的に行うので、resetメソッドを呼び出す必要はありません。

* `MediaPlayer`がERRORステータスで、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >これは、ERRORステータスから回復する唯一の方法です。

1. `reset`を呼び出して、`MediaPlayer`インスタンスを初期化されていない状態に戻します。

   ```
   function reset():void; 
   ```

1. `MediaPlayer.replaceCurrentItem`または`MediaPlayer.replaceCurrentResource`を使用して、別の`MediaResource`を読み込みます。

   >[!TIP]
   >
   >エラーをクリアするには、同じ`MediaResource`を読み込みます。

1. `MediaPlaybackStatusChangeEvent.STATUS_CHANGED`を`PREPARED`ステータスで受け取ったら、再生を開始します。
