---
description: ABR 制御値は ABRControlParameters でのみ設定できますが、新しい値をいつでも作成できます。
title: ABRControlParameters を使用したアダプティブビットレートの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# ABRControlParameters を使用したアダプティブビットレートの設定{#configure-adaptive-bit-rates-using-abrcontrolparameters}

ABR 制御値は ABRControlParameters でのみ設定できますが、新しい値をいつでも作成できます。

次の条件が適用されます。 `ABRControlParameters`:

* 構築時にすべてのパラメータの値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合、 `ArgumentError` がスローされます。

1. ABR ポリシーを決定します。

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. ABR パラメーター値を `ABRControlParameters` コンストラクターに割り当てて、Media Player に割り当てます。

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```
