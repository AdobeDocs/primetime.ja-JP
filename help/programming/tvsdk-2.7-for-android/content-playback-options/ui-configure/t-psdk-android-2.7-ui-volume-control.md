---
description: ビデオのボリュームを調整するユーザーインターフェイスコントロールを設定できます。
seo-description: ビデオのボリュームを調整するユーザーインターフェイスコントロールを設定できます。
seo-title: ボリューム制御の提供
title: ボリューム制御の提供
uuid: f1e959e0-1817-4ccb-8adc-3eba09c91887
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

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

