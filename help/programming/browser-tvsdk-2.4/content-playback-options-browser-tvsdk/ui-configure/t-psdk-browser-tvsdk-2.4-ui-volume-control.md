---
description: サウンドの音量を制御するユーザインターフェイスを設定できます。
title: ボリューム制御の提供
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '87'
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

