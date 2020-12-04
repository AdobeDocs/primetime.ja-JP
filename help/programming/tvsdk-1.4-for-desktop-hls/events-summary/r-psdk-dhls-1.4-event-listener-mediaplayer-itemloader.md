---
description: TVSDKは、メディア項目の読み込みに応じて、メディアプレイヤー項目イベントをディスパッチします。
seo-description: TVSDKは、メディア項目の読み込みに応じて、メディアプレイヤー項目イベントをディスパッチします。
seo-title: Loaderイベント
title: Loaderイベント
uuid: 0ad37715-14b1-457c-892f-0db0d6220f0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# ローダイベント{#loader-events}

TVSDKは、メディア項目の読み込みに応じて、メディアプレイヤー項目イベントをディスパッチします。

これらのイベントは、代替ワークフローを提供します。 `MediaPlayer`を作成する際に、このインターフェイスを実装する必要はありません。 `MediaPlayerItemLoader`を使いたい場合に使用します。

メディアプレイヤーリソースの読み込みに関連するイベントに関して通知を受けるには、以下のイベントのリスナーを`MediaPlayerItemLoader`オブジェクトに登録します。

| イベント | 意味 |
|---|---|
| MediaPlayerItemLoader.[completed](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:completed) | メディアリソースの読み込みが正常に完了しました。 |
| MediaPlayerItemLoader.[failed](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html#event:failed) | メディアリソースの読み込みで問題が発生しました。 |