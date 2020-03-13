---
description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-title: 有効なステータスを待つ
title: 有効なステータスを待つ
uuid: ffa63ad6-84d3-4eb2-aa99-026418d86528
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 有効な状態を待つ {#wait-for-a-valid-state}

TVSDKを使用すると、ライブおよびビデオオンデマンド(VOD)の基本的な再生エクスペリエンスを制御できます。 TVSDKは、プレイヤーインスタンスにメソッドとプロパティを提供します。このメソッドを使用して、プレイヤーのユーザーインターフェイスを設定できます。

ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。

プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことを確認できます。 プレイヤーが少なくとも必要なステータスになっていない場合は、多くのプレーヤーメソッドがスローしま `MediaPlayerException`す。

必要なステータスは、通常はPREPAREDです。 この場合、コールバックルーチンが実行さ `StatusChangeEventListener.onStatusChanged()` れます。

1. ステータスを確認するには、を `PREPARED`確認しま `MediaPlayer.MediaPlayerStatus`す。
