---
description: サウンドの音量を制御するユーザインターフェイスを設定できます。
title: ボリューム制御の提供
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# ボリューム制御{#provide-volume-control}を提供

サウンドの音量を制御するユーザインターフェイスを設定できます。

1. MediaPlayerインスタンスがこのコマンドに対して有効な状態になるのを待ちます。この状態は、RELEASEDまたはERROR以外です。
1. `MediaPlayer`インスタンスで`setVolume`を呼び出して、オーディオのボリュームを設定します。

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。0は無音、100は最大です。

