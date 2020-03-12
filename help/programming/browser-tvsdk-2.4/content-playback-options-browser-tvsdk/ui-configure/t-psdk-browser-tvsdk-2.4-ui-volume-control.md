---
description: サウンドのボリュームを制御するユーザインターフェイスを設定できます。
seo-description: サウンドのボリュームを制御するユーザインターフェイスを設定できます。
seo-title: ボリューム制御の提供
title: ボリューム制御の提供
uuid: 5f2f69cc-3969-4ca2-8ab9-5713fdf5cdb8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ボリューム制御の提供{#provide-volume-control}

サウンドのボリュームを制御するユーザインターフェイスを設定できます。

1. このコマンドで `MediaPlayer` インスタンスが有効な状態になるまで待ちます。

   RELEASEDまたはERROR以外の状態はすべて有効です。
1. インスタンスのボリューム属性を設定し `MediaPlayer` て、オーディオボリュームを設定します。

   ```js
   player.volume = ...
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。0は無音で最大ボリュームです。

