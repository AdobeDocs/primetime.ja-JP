---
description: Browser TVSDK Player のほとんどのメソッドを使用するには、そのプレーヤーが有効な状態にある必要があります。
title: 有効な状態になるのを待つ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 有効な状態になるのを待つ {#wait-for-a-valid-state}

Browser TVSDK Player のほとんどのメソッドを使用するには、そのプレーヤーが有効な状態にある必要があります。

プレーヤーが様々な状態を移動します。 プレーヤーが正しい状態になるのを待つことで、メディアリソースが正常に読み込まれたことを確認します。 プレーヤーが少なくとも必要な状態にない場合は、多くのプレーヤーメソッドがスローします `IllegalStateException`.

通常、必要な状態は PREPARED です。

1. 状態が PREPARED であることを確認するには：

   プレーヤーを初期化する際に、Browser TVSDK が `AdobePSDK.MediaPlayerStatusChangeEvent` イベント `event.status` / `MediaPlayerStatus.PREPARED`.

   MediaPlayer オブジェクトの現在の状態が PREPARED 以上かどうかを確認する。

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```
