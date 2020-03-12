---
description: TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。
seo-description: TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。
seo-title: ローダイベント
title: ローダイベント
uuid: 0ad37715-14b1-457c-892f-0db0d6220f0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# ローダイベント{#loader-events}

TVSDKは、メディア項目の読み込みに応答して、メディアプレイヤー項目イベントをディスパッチします。

これらのイベントは、別のワークフローを提供します。 を作成する際に、このインターフェイスを実装する必要はありませ `MediaPlayer`ん。 これは、を使用する場合に使用しま `MediaPlayerItemLoader`す。

メディアプレイヤーリソースの読み込みに関連するイベントの通知を受け取るには、次のイベントのリスナーをオブジェクトに登録 `MediaPlayerItemLoader` します。

| イベント | 意味 |
|---|---|
| MediaPlayerItemLoader.[完了](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | メディアリソースの読み込みが正常に完了しました。 |
| MediaPlayerItemLoader.[失敗](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | メディアリソースの読み込みで問題が発生しました。 |