---
description: ほとんどの TVSDK プレーヤーメソッドを使用する前に、プレーヤーのステータスが有効である必要があります。
title: 有効な状態になるのを待つ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# 有効な状態になるのを待つ{#wait-for-a-valid-state}

ほとんどの TVSDK プレーヤーメソッドを使用する前に、プレーヤーのステータスが有効である必要があります。

プレーヤーが様々なステータスを切り替えます。 プレーヤーが正しいステータスになるのを待つことで、メディアリソースが正常に読み込まれたことを確認できます。 プレーヤーが少なくとも必要なステータスにない場合は、多くのプレーヤーメソッドがスローします `IllegalStateException`.

通常、必須ステータスは `PTMediaPlayerStatusReady`.
