---
description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。
title: ABRControlParametersを使用した可変ビットレートの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---


# ABRControlParameters{#configure-adaptive-bit-rates-using-abrcontrolparameters}を使用して可変ビットレートを設定

ABR制御値はABRControlParametersでのみ設定できますが、新しい値をいつでも作成できます。

`ABRControlParameters`には次の条件が適用されます。

* 構築時に、すべてのパラメーターに値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合は、`ArgumentError`がスローされます。

1. ABRポリシーの決定：

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. ABRパラメーターの値を`ABRControlParameters`コンストラクターに設定し、それらをメディアプレイヤーに割り当てます。

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```

