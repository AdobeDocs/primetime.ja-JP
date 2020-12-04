---
description: サウンドの音量を制御するユーザインターフェイスを設定できます。
seo-description: サウンドの音量を制御するユーザインターフェイスを設定できます。
seo-title: ボリューム制御の提供
title: ボリューム制御の提供
uuid: 5f2f69cc-3969-4ca2-8ab9-5713fdf5cdb8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---


# ボリューム制御{#provide-volume-control}を提供

サウンドの音量を制御するユーザインターフェイスを設定できます。

1. `MediaPlayer`インスタンスがこのコマンドに対して有効な状態になるのを待ちます。

   RELEASEDまたはERROR以外の状態はすべて有効です。
1. `MediaPlayer`インスタンスのボリューム属性を設定して、オーディオのボリュームを設定します。

   ```js
   player.volume = ...
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。0は無音で最大ボリュームです。

