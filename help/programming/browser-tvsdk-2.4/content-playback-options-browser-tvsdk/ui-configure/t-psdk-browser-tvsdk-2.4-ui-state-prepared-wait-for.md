---
description: ブラウザーTVSDKプレーヤーのほとんどのメソッドを使用する前に、プレーヤーが有効な状態である必要があります。
seo-description: ブラウザーTVSDKプレーヤーのほとんどのメソッドを使用する前に、プレーヤーが有効な状態である必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: 0add29a8-fbd8-483a-8c99-e4bc6de9e3d3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 有効な状態を待つ {#wait-for-a-valid-state}

ブラウザーTVSDKプレーヤーのほとんどのメソッドを使用する前に、プレーヤーが有効な状態である必要があります。

プレイヤーは様々な状態を移動します。 プレイヤーが正しい状態になるのを待つと、メディアリソースが正常に読み込まれたことを確認できます。 プレーヤーが少なくとも必要な状態にない場合、多くのプレーヤーメソッドがスローしま `IllegalStateException`す。

通常、必要な状態はPREPAREDです。

1. 状態がPREPAREDであることを確認するには：

   プレイヤーが初期化中に、ブラウザーTVSDKがイベントをディスパッチするま `AdobePSDK.MediaPlayerStatusChangeEvent` で待ちます(「」を `event.status` 含む) `MediaPlayerStatus.PREPARED`。

   MediaPlayerオブジェクトの現在の状態がPREPAREDであるかどうかを確認する場合。

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```

