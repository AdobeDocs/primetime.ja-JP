---
description: ビデオのボリュームを調整するユーザインターフェイスコントロールを設定できます。
seo-description: ビデオのボリュームを調整するユーザインターフェイスコントロールを設定できます。
seo-title: ボリューム制御の提供
title: ボリューム制御の提供
uuid: f1e959e0-1817-4ccb-8adc-3eba09c91887
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# ボリューム制御の提供 {#provide-volume-control}

ビデオのボリュームを調整するユーザインターフェイスコントロールを設定できます。

1. ボリューム制御インターフェイス要素のコールバックルーチンで、プレーヤーがこのコマンドに対して有効なステータスであることを確認します。

   >[!TIP]
   >
   >RELEASED以外のステータスはすべて有効です。

1. を呼び出し `setVolume` て、オーディオのボリュームを設定します。

   例：

   ```java
   void setVolume(int volume) throws MediaPlayerException;
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。ここで、は無 `0` 音で最大ボ `1` リュームを表します。

