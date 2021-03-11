---
description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
title: 有効な状態を待つ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---


# 有効な状態を待つ{#wait-for-a-valid-state}

TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。

プレイヤーは様々なステータスを通り抜けます。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドは`IllegalStateException`をスローします。

必要なステータスは通常`PTMediaPlayerStatusReady`です。
