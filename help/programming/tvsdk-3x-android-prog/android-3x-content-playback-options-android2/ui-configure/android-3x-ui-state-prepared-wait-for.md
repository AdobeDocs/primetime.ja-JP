---
description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-title: 有効なステータスを待つ
title: 有効なステータスを待つ
uuid: 7a86b4cf-f7a0-4d90-9ff2-401640a395c5
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 有効なステータスを待つ {#wait-for-a-valid-status}

TVSDKを使用すると、ライブおよびビデオオンデマンド(VOD)の基本的な再生エクスペリエンスを制御できます。 TVSDKは、プレイヤーインスタンスにメソッドとプロパティを提供します。このメソッドを使用して、プレイヤーのユーザーインターフェイスを設定できます。

ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。

プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことを確認できます。 プレイヤーが少なくとも必要なステータスになっていない場合は、多くのプレーヤーメソッドがスローしま `MediaPlayerException`す。

必要なステータスは、通常はPREPAREDです。 この場合、コールバックルーチンが実行さ `StatusChangeEventListener.onStatusChanged()` れます。

ステータスを確認するには、を `PREPARED`確認しま `MediaPlayer.MediaPlayerStatus`す。