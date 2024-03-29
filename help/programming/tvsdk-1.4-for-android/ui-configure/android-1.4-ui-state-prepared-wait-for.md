---
description: TVSDK を使用して、ライブおよびビデオオンデマンド (VOD) の基本的な再生エクスペリエンスを制御できます。 TVSDK は、プレーヤーインスタンス上のメソッドとプロパティを提供します。このメソッドを使用して、プレーヤーユーザーインターフェイスを設定できます。
title: 有効な状態になるのを待つ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# 有効な状態になるのを待つ {#wait-for-a-valid-state}

TVSDK を使用して、ライブおよびビデオオンデマンド (VOD) の基本的な再生エクスペリエンスを制御できます。 TVSDK は、プレーヤーインスタンス上のメソッドとプロパティを提供します。このメソッドを使用して、プレーヤーユーザーインターフェイスを設定できます。

ほとんどの TVSDK プレーヤーメソッドを使用する前に、プレーヤーが有効な状態にある必要があります。
プレーヤーが様々な状態を移動します。 プレーヤーが正しい状態になるのを待つことで、メディアリソースが正常に読み込まれたことを確認します。 プレーヤーが少なくとも必要な状態にない場合は、多くのプレーヤーメソッドがスローします `IllegalStateException`.

通常、必要な状態は PREPARED です。
