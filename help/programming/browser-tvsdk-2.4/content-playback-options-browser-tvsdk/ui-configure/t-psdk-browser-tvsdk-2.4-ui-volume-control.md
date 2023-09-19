---
description: サウンドボリュームのユーザインターフェイスコントロールを設定できます。
title: ボリューム制御を提供
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# ボリューム制御を提供{#provide-volume-control}

サウンドボリュームのユーザインターフェイスコントロールを設定できます。

1. 待機： `MediaPlayer` インスタンスがこのコマンドに対して有効な状態になっている。

   RELEASED または ERROR 以外の状態は有効です。
1. のボリューム属性を設定します。 `MediaPlayer` インスタンス：オーディオのボリュームを設定します。

   ```js
   player.volume = ...
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの比率で表します。0 は無音で、最大ボリュームです。
