---
description: ABR 制御値は ABRControlParameters でのみ設定できますが、新しい値をいつでも作成できます。
title: ABRControlParameters を使用したアダプティブビットレートの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# ABRControlParameters を使用したアダプティブビットレートの設定 {#configure-adaptive-bit-rates-using-abrcontrolparameters}

ABR 制御値は ABRControlParameters でのみ設定できますが、新しい値をいつでも作成できます。

次の条件が適用されます。 `ABRControlParameters`:

* 構築時に、すべてのパラメータの値を指定する必要があります。
* 構築後は、個々の値を変更できません。
* 指定したパラメーターが許容範囲外の場合、 `ArgumentError` がスローされます。

1. 初期、最小、最大のビットレートを決定します。
1. ABR ポリシーを決定します。

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. ABR パラメーター値を `ABRControlParameters` コンストラクターを使用して、Media Player に値を割り当てます。

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
