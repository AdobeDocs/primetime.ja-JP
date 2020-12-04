---
description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: ad9df366-c443-4e6b-a7ab-658d5691eb94
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# 有効な状態を待つ{#wait-for-a-valid-state}

TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。

プレイヤーは様々なステータスを通り抜けます。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドは`IllegalStateException`をスローします。

必要なステータスは通常`PTMediaPlayerStatusReady`です。