---
description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: e13201d7-b217-4d01-bdb7-a71855e3500e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# 有効な状態を待つ{#wait-for-a-valid-state}

TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。

プレイヤーは様々なステータスを通り抜けます。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドは`IllegalStateException`をスローします。

必要なステータスは通常`PTMediaPlayerStatusReady`です。
