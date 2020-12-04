---
description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。
seo-description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。
seo-title: ABRControlParametersを使用した可変ビットレートの設定
title: ABRControlParametersを使用した可変ビットレートの設定
uuid: c877c5cc-ad72-46dc-afc4-d41ee097a9a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}を使用して可変ビットレートを設定

ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。

`ABRControlParameters`には次の条件が適用されます。

* 構築時に、すべてのパラメーターに値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合は、`ArgumentError`がスローされます。

1. 初期、最小および最大ビットレートを決定します。
1. ABRポリシーの決定：

   * `ABR_CONSERVATIVE`
   * `ABR_MODERATE`
   * `ABR_AGGRESSIVE`

1. ABRパラメーターの値を`ABRControlParameters`コンストラクターに設定し、それらをメディアプレイヤーに割り当てます。

   ```java
   public ABRControlParameters(int initialBitRate, 
     int minBitRate, 
     int maxBitRate, 
     ABRControlParameters.ABRPolicy abrPolicy, 
     int minTrickPlayBitRate, 
     int maxTrickPlayBitRate, 
     int maxTrickPlayBandwidthUsage, 
     int maxPlayoutRate);
   ```

