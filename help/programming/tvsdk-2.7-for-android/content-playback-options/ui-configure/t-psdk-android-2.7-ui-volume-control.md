---
description: ビデオのボリュームを調整するユーザーインターフェイスコントロールを設定できます。
title: ボリューム制御を提供
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# ボリューム制御を提供 {#provide-volume-control}

ビデオのボリュームを調整するユーザーインターフェイスコントロールを設定できます。

1. ボリューム制御インターフェイス要素のコールバックルーチンで、プレーヤーがこのコマンドの有効なステータスになっていることを確認します。

   >[!TIP]
   >
   >RELEASED を除くステータスはすべて有効です。

1. 通話 `setVolume` オーディオのボリュームを設定します。

   例：

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。ここで、 `0` 静かで `1` は、最大ボリュームです。
