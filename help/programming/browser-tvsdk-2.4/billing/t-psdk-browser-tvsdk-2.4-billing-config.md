---
description: デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、メディアプレイヤーを初期化する前に、BillingMetricsConfigurationクラスを使用してこれらのパラメーターを設定します。
seo-description: デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、メディアプレイヤーを初期化する前に、BillingMetricsConfigurationクラスを使用してこれらのパラメーターを設定します。
seo-title: 請求指標の設定
title: 請求指標の設定
uuid: 04d3b53e-f08c-49d0-ba42-5375f1307d2e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---


# 請求指標の設定{#configure-billing-metrics}

デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、メディアプレイヤーを初期化する前に、BillingMetricsConfigurationクラスを使用してこれらのパラメーターを設定します。

ほとんどのお客様は、デフォルトの設定を使用する必要があります。

>[!IMPORTANT]
>
>設定した設定は、メディアプレイヤーの使用期間中有効です。 メディアプレイヤーを初期化した後は、設定を変更できません。

請求指標を設定するには：

* 次のコードサンプルを入力します。

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.billingMetricsConfiguration.isEnabled = true; 
   config.billingMetricsConfiguration.proVODBillableDurationMinutes = 60; 
   config.billingMetricsConfiguration.stdVODBillableDurationMinutes = 30; 
   config.billingMetricsConfiguration.liveBillableDurationMinutes = 15; 
   _player.replaceCurrentResource(_resource, config);
   ```

   `_player`は`AdobePSDK.MediaPlayer`のインスタンス、`_resource`は`AdobePSDK.MediaResource`のインスタンスです。

