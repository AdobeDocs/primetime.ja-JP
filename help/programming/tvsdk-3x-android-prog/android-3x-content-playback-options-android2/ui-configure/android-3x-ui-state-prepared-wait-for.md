---
description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
title: 有効なステータスを待つ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 有効なステータスを待つ{#wait-for-a-valid-status}

TVSDKを使用して、ライブおよびビデオオンデマンド(VOD)の基本的な再生エクスペリエンスを制御できます。 TVSDKは、プレイヤーインスタンスにメソッドとプロパティを提供します。このメソッドとプロパティを使用して、プレイヤーユーザーインターフェイスを設定できます。

TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。

プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドは`MediaPlayerException`をスローします。

必要なステータスは、通常PREPAREDです。 この場合、`StatusChangeEventListener.onStatusChanged()`のコールバックルーチンが実行されます。

ステータスが`PREPARED`であることを確認するには、`MediaPlayer.MediaPlayerStatus`をチェックします。