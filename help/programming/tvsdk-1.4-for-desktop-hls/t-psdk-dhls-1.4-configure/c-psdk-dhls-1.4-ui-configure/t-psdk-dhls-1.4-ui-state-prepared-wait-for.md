---
description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-description: TVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーのステータスが有効である必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: 918ab021-3685-424a-b84e-683da0357724
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---


# 有効な状態を待つ{#wait-for-a-valid-state}

TVSDKを使用して、ライブおよびビデオオンデマンド(VOD)の基本的な再生エクスペリエンスを制御できます。 TVSDKは、プレイヤーユーザーインターフェイスの設定に使用できるプレイヤーインスタンスにメソッドとプロパティを提供します。TVSDKプレイヤーメソッドのほとんどを使用する前に、プレイヤーが有効なステータスになっている必要があります。

プレイヤーは様々なステータスを通り抜けます。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドは`IllegalStateException`をスローします。

必要なステータスは、通常PREPAREDです。

1. ステータスがPREPAREDであることを確認するには：

   プレイヤーが初期化中に、TVSDKがPREPAREDステータスで`MediaPlayerStatusChangeEvent.STATUS_CHANGED`イベントのコールバックを呼び出すまで待ちます。

   `MediaPlayer`オブジェクトの現在のステータスがPREPARED以上かどうかを確認する。

   ```
   function getstatus():String;
   ```
