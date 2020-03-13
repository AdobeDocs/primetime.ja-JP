---
description: TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。
seo-description: TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。
seo-title: ローダイベント
title: ローダイベント
uuid: 1b401ff5-4313-4c64-8be9-99bdeb58ba2a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ローダイベント{#loader-events}

TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。

これらのイベントは、別のワークフローを提供します。 MediaPlayerを作成する際に、このインターフェイスを実装する必要はありません。 これは、を使用する場合に使用しま `MediaPlayerItemLoader`す。

メディアプレイヤーリソースの読み込みに関するイベントの通知を受け取るには、以下のイベントを含む `MediaPlayerItemLoader.LoaderListener` 実装を登録します。

| イベント | 意味 |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([mediaPlayerItem](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) playerItem) | メディアリソースの読み込みが正常に完了しました。 |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | メディアリソースの読み込みで問題が発生しました。 |

>[!NOTE]
>
>「QoSイベント」 `onLoadInfo (loadInfo)` の項も参照してください。

