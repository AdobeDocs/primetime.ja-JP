---
description: サウンドボリュームのユーザインターフェイスコントロールを設定できます。
title: ボリューム制御を提供
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# ボリューム制御を提供{#provide-volume-control}

サウンドボリュームのユーザインターフェイスコントロールを設定できます。

1. MediaPlayer インスタンスがこのコマンドの有効な状態になるのを待ちます（RELEASED または ERROR を除く）。
1. 通話 `setVolume` の `MediaPlayer` インスタンス：オーディオのボリュームを設定します。

   ```java
   void setVolume(int volume) throws IllegalStateException;
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの比率で表します。0 は無音、100 は最大ボリュームです。
