---
description: サウンドの音量を制御するユーザインターフェイスを設定できます。
seo-description: サウンドの音量を制御するユーザインターフェイスを設定できます。
seo-title: ボリューム制御の提供
title: ボリューム制御の提供
uuid: 63e96424-54d0-4c16-bd94-2366722f752a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '97'
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

