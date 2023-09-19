---
description: ほとんどの TVSDK プレーヤーメソッドを使用する前に、プレーヤーのステータスが有効である必要があります。
title: 有効な状態になるのを待つ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# 有効な状態になるのを待つ {#wait-for-a-valid-state}

TVSDK を使用して、ライブおよびビデオオンデマンド (VOD) の基本的な再生エクスペリエンスを制御できます。 TVSDK は、プレーヤーインスタンス上にメソッドとプロパティを提供します。これを使用して、プレーヤーユーザーインターフェイスを設定できます。 TVSDK プレーヤーメソッドのほとんどを使用する前に、プレーヤーが有効なステータスになっている必要があります。

プレーヤーが様々なステータスを切り替えます。 プレーヤーが正しいステータスになるのを待つことで、メディアリソースが正常に読み込まれたことを確認できます。 プレーヤーが少なくとも必要なステータスにない場合、多くのプレーヤーメソッドはスローします `IllegalStateException`.

通常、必要なステータスは PREPARED です。

1. ステータスが「準備済み」であることを確認するには：

   プレーヤーの初期化中に、 TVSDK が `MediaPlayerStatusChangeEvent.STATUS_CHANGED` イベントのステータスが PREPARED の場合。

   現在のステータスが `MediaPlayer` オブジェクトが少なくとも準備済みです。

   ```
   function getstatus():String;
   ```
