---
description: TVSDK は、メディアアイテムの読み込みに応じて、メディアプレーヤーアイテムのイベントをディスパッチします。
title: Loader イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# Loader イベント{#loader-events}

TVSDK は、メディアアイテムの読み込みに応じて、メディアプレーヤーアイテムのイベントをディスパッチします。

これらのイベントは、別のワークフローを提供します。 MediaPlayer を作成する際に、このインターフェイスを実装する必要はありません。 これは、 `MediaPlayerItemLoader`.

メディアプレーヤーリソースの読み込みに関連するイベントに関する通知を受け取るには、 `MediaPlayerItemLoader.LoaderListener` 次のイベントを含む。

| イベント | 意味 |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | メディアリソースの読み込みが正常に完了しました。 |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | メディアリソースの読み込み中に問題が発生しました。 |

>[!NOTE]
>
>関連トピック `onLoadInfo (loadInfo)` QoS イベントの下で
