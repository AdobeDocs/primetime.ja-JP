---
description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-title: 有効なステータスを待つ
title: 有効なステータスを待つ
uuid: ffa63ad6-84d3-4eb2-aa99-026418d86528
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# 有効な状態を待つ{#wait-for-a-valid-state}

TVSDKを使用して、ライブおよびビデオオンデマンド(VOD)の基本的な再生エクスペリエンスを制御できます。 TVSDKは、プレイヤーインスタンスにメソッドとプロパティを提供します。このメソッドとプロパティを使用して、プレイヤーユーザーインターフェイスを設定できます。

TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。

プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドは`MediaPlayerException`をスローします。

必要なステータスは、通常PREPAREDです。 この場合、`StatusChangeEventListener.onStatusChanged()`のコールバックルーチンが実行されます。

1. ステータスが`PREPARED`であることを確認するには、`MediaPlayer.MediaPlayerStatus`をチェックします。
