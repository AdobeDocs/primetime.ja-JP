---
description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: ad9df366-c443-4e6b-a7ab-658d5691eb94
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d

---


# 有効な状態を待つ {#wait-for-a-valid-state}

ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。

プレイヤーは様々なステータスを経て移動します。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことを確認できます。 プレイヤーが少なくとも必要なステータスになっていない場合は、多くのプレーヤーメソッドがスローしま `IllegalStateException`す。

通常、必須ステータスはで `PTMediaPlayerStatusReady`す。