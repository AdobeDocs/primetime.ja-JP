---
description: ほとんどの TVSDK プレーヤーメソッドを使用する前に、プレーヤーのステータスが有効である必要があります。
title: 有効なステータスを待つ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# 有効な状態になるのを待つ {#wait-for-a-valid-state}

TVSDK を使用すると、ライブおよびビデオオンデマンド (VOD) の基本的な再生エクスペリエンスを制御できます。 TVSDK は、プレーヤーインスタンス上のメソッドとプロパティを提供します。このメソッドを使用して、プレーヤーユーザーインターフェイスを設定できます。

ほとんどの TVSDK プレーヤーメソッドを使用する前に、プレーヤーのステータスが有効である必要があります。

プレーヤーが正しいステータスになるのを待つことで、メディアリソースが正常に読み込まれたことを確認できます。 プレーヤーが少なくとも必要なステータスにない場合は、多くのプレーヤーメソッドがスローします `MediaPlayerException`.

通常、必要なステータスは PREPARED です。 この場合、 `StatusChangeEventListener.onStatusChanged()` を実行します。

1. ステータスが「 `PREPARED`, check `MediaPlayer.MediaPlayerStatus`.
