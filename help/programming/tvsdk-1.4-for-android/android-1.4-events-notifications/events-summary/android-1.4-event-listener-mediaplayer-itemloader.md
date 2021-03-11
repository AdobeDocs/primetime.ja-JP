---
description: TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。
title: Loaderイベント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# ローダイベント{#loader-events}

TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。

これらのイベントは、代替ワークフローを提供します。 MediaPlayerの作成時に、このインターフェイスを実装する必要はありません。 `MediaPlayerItemLoader`を使いたい場合に使用します。

メディアプレイヤーリソースの読み込みに関するイベント通知を受け取るには、以下のイベントを含む`MediaPlayerItemLoader.LoaderListener`の実装を登録します。

| イベント | 意味 |
|---|---|
| [onLoadComplete](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onLoadComplete(com.adobe.mediacore.MediaPlayerItem))([](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html) mediaPlayerItemplayerItem) | メディアリソースの読み込みが正常に完了しました。 |
| [onError](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html#onError(com.adobe.ave.MediaErrorCode,%20java.lang.String)) | メディアリソースの読み込みで問題が発生しました。 |

>[!NOTE]
>
>QoSイベントの`onLoadInfo (loadInfo)`も参照してください。

