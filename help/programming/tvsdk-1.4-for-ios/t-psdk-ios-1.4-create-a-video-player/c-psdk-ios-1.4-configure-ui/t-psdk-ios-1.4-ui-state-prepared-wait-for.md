---
description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: e13201d7-b217-4d01-bdb7-a71855e3500e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 有効な状態を待つ{#wait-for-a-valid-state}

ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。

プレイヤーは様々なステータスを経て移動します。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことを確認できます。 プレイヤーが少なくとも必要なステータスになっていない場合は、多くのプレーヤーメソッドがスローしま `IllegalStateException`す。

通常、必須ステータスはで `PTMediaPlayerStatusReady`す。
