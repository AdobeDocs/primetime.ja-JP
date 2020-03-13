---
description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-description: ほとんどのTVSDKプレーヤーメソッドを使用する前に、プレーヤーが有効なステータスになっている必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: 918ab021-3685-424a-b84e-683da0357724
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# 有効な状態を待つ {#wait-for-a-valid-state}

TVSDKを使用すると、ライブおよびビデオオンデマンド(VOD)の基本的な再生エクスペリエンスを制御できます。 TVSDKは、プレイヤーインスタンスにメソッドとプロパティを提供します。このメソッドを使用して、プレイヤーのユーザーインターフェイスを設定できます。TVSDKプレイヤーメソッドのほとんどを使用する前に、プレイヤーが有効なステータスである必要があります。

プレイヤーは様々なステータスを経て移動します。 プレイヤーが正しいステータスになるのを待つと、メディアリソースが正常に読み込まれたことを確認できます。 プレイヤーが少なくとも必要なステータスになっていない場合、多くのプレーヤーメソッドはスローしま `IllegalStateException`す。

必要なステータスは、通常はPREPAREDです。

1. ステータスがPREPAREDであることを確認するには：

   プレイヤーが初期化中に、TVSDKがイベントのコールバックをPREPAREDステータスで呼び出す `MediaPlayerStatusChangeEvent.STATUS_CHANGED` まで待ちます。

   オブジェクトの現在のステータスがPREPAREDであ `MediaPlayer` るかどうかを確認する。

   ```
   function getstatus():String;
   ```
