---
description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値はいつでも作成できます。
seo-description: ABR制御値はABRControlParametersでのみ設定できますが、新しい値はいつでも作成できます。
seo-title: ABRControlParametersを使用した可変ビットレートの設定
title: ABRControlParametersを使用した可変ビットレートの設定
uuid: 99b7a463-327b-48bf-8244-e41467072b44
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ABRControlParametersを使用した可変ビットレートの設定{#configure-adaptive-bit-rates-using-abrcontrolparameters}

ABR制御値はABRControlParametersでのみ設定できますが、新しい値はいつでも作成できます。

次の条件が適用されま `ABRControlParameters`す。

* 構築時に、すべてのパラメーターの値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合は、がスロー `ArgumentError` されます。

1. ABRポリシーの決定：

   * `ABRControlParameters.CONSERVATIVE_POLICY`
   * `ABRControlParameters.MODERATE_POLICY`
   * `ABRControlParameters.AGGRESSIVE_POLICY`

1. ABRパラメーターの値をコンストラク `ABRControlParameters` ターに設定し、Media Playerに割り当てます。

   ```js
   var abrParams = new AdobePSDK.ABRControlParameters(); 
   abrParams.initialBitRate = nInitialBitRate; 
   abrParams.minBitRate = nMinBitRate; 
   abrParams.maxBitRate = nMaxBitRate; 
   abrParams.abrPolicy = eABRPolicy; 
   player.abrControlParameters = abrParams;
   ```

