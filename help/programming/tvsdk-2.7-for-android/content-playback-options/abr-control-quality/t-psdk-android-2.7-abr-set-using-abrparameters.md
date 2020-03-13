---
description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値はいつでも作成できます。
seo-description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値はいつでも作成できます。
seo-title: ABRControlParametersを使用した可変ビットレートの設定
title: ABRControlParametersを使用した可変ビットレートの設定
uuid: 7084e954-196b-492e-846f-f8b36bed13a9
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# ABRControlParametersを使用した可変ビットレートの設定 {#configure-adaptive-bit-rates-using-abrcontrolparameters}

ABR制御値はABRControlParametersでのみ設定できますが、新しい値はいつでも作成できます。

次の条件が適用されま `ABRControlParameters`す。

* 構築時に、すべてのパラメーターの値を指定する必要があります。
* 構築後は、個々の値を変更できません。
* 指定したパラメーターが許容範囲外の場合は、がスロー `ArgumentError` されます。

1. 初期、最小、最大のビットレートを決定します。
1. ABRポリシーの決定：

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. コンストラクターにABRパラメーターの値 `ABRControlParameters` を設定し、その値をメディアプレイヤーに割り当てます。

   ```
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```

