---
description: ビデオのボリュームを調整するユーザーインターフェイスコントロールを設定できます。
title: ボリューム制御の提供
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 2%

---


# ボリューム制御を提供{#provide-volume-control}

ビデオのボリュームを調整するユーザーインターフェイスコントロールを設定できます。

1. ボリューム制御インターフェイス要素のコールバックルーチンで、プレイヤーがこのコマンドに対して有効なステータスにあることを確認します。

   >[!TIP]
   >
   >RELEASED以外のステータスはすべて有効です。

1. `setVolume`を呼び出して、オーディオのボリュームを設定します。

   例：

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。`0`は無音、`1`は最大ボリュームです。