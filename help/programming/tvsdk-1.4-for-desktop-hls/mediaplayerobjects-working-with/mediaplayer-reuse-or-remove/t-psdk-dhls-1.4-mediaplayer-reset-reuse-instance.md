---
description: MediaPlayer インスタンスをリセットすると、 MediaPlayerStatus で定義されている、初期化されていない IDLE 状態に戻されます。
title: MediaPlayer インスタンスのリセットまたは再利用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# MediaPlayer インスタンスのリセットまたは再利用{#reset-or-reuse-a-mediaplayer-instance}

不要になった MediaPlayer インスタンスをリセット、再利用、またはリリースできます。

MediaPlayer インスタンスをリセットすると、 MediaPlayerStatus で定義されている、初期化されていない IDLE 状態に戻されます。

この操作は、次の場合に役立ちます。

* 次の項目を再利用します： `MediaPlayer` インスタンスを使用するが、新しい `MediaResource` （ビデオコンテンツ）をクリックし、前のインスタンスを置き換えます。

  リセットを使用すると、 `MediaPlayer` リソースを解放するオーバーヘッドがなく、 `MediaPlayer`、およびリソースの再割り当て。 The `replaceCurrentItem` および `replaceCurrentResource` メソッドは、reset メソッドを呼び出すことなく、これらの手順を自動的に実行します。

* 次の場合に `MediaPlayer` は ERROR ステータスなので、クリアする必要があります。

  >[!IMPORTANT]
  >
  >これは、ERROR ステータスから回復する唯一の方法です。

1. 通話 `reset` 返す `MediaPlayer` インスタンスを初期化されていない状態に変更します。

   ```
   function reset():void; 
   ```

1. 用途 `MediaPlayer.replaceCurrentItem` または `MediaPlayer.replaceCurrentResource` 別の物を積み込む `MediaResource`.

   >[!TIP]
   >
   >エラーをクリアするには、同じ `MediaResource`.

1. この `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` と `PREPARED` ステータス、再生を開始します。
