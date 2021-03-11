---
description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。
title: ABRControlParametersを使用した可変ビットレートの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# ABRControlParameters {#configure-adaptive-bit-rates-using-abrcontrolparameters}を使用して可変ビットレートを設定

ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。

`ABRControlParameters`には次の条件が適用されます。

* 構築時に、すべてのパラメーターに値を指定する必要があります。
* 構築後は、個々の値を変更できません。
* 指定したパラメーターが許容範囲外の場合は、`ArgumentError`がスローされます。

1. 初期、最小および最大ビットレートを決定します。
1. ABRポリシーの決定：

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. ABRパラメーターの値を`ABRControlParameters`コンストラクターに設定し、値をメディアプレイヤーに割り当てます。

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
