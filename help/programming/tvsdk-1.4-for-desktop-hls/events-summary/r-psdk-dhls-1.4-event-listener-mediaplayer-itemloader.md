---
description: TVSDK は、メディアアイテムの読み込みに応じて、メディアプレーヤーアイテムのイベントをディスパッチします。
title: Loader イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Loader イベント{#loader-events}

TVSDK は、メディアアイテムの読み込みに応じて、メディアプレーヤーアイテムのイベントをディスパッチします。

これらのイベントは、別のワークフローを提供します。 このインターフェイスは、 `MediaPlayer`. これは、 `MediaPlayerItemLoader`.

メディアプレーヤーリソースの読み込みに関連するイベントに関する通知を受け取るには、以下のイベントのリスナーを `MediaPlayerItemLoader` オブジェクト。

| イベント | 意味 |
|---|---|
| MediaPlayerItemLoader.[完了](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | メディアリソースの読み込みが正常に完了しました。 |
| MediaPlayerItemLoader.[失敗](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | メディアリソースの読み込み中に問題が発生しました。 |
