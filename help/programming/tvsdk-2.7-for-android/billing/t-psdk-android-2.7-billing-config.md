---
description: デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、メディアプレイヤーを初期化する前に、BillingMetricsConfigurationクラスを使用してこれらのパラメーターを設定します。
seo-description: デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、メディアプレイヤーを初期化する前に、BillingMetricsConfigurationクラスを使用してこれらのパラメーターを設定します。
seo-title: 請求指標の設定
title: 請求指標の設定
uuid: d8656ab2-fdd8-4fe4-8578-a6c8ecd378e2
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# 請求指標の設定{#configure-billing-metrics}

デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、メディアプレイヤーを初期化する前に、BillingMetricsConfigurationクラスを使用してこれらのパラメーターを設定します。

>[!TIP]
>
>ほとんどのお客様は、デフォルトの設定を使用する必要があります。

>[!IMPORTANT]
>
>設定した設定は、メディアプレイヤーの使用期間中有効です。 メディアプレイヤーを初期化した後は、設定を変更できません。

請求指標を設定するには：

1. 次のコードサンプルを入力します。

   ```java
   MediaPlayerItemConfig config = new MediaPlayerItemConfig(); 
   BillingMetricsConfiguration billingConfig = new BillingMetricsConfiguration(); 
   billingConfig.setEnabled(true); 
   billingConfig.setProVODBillableDurationMinutes(60); 
   billingConfig.setStdVODBillableDurationMinutes(30); 
   billingConfig.setLiveBillableDurationMinutes(15); 
   config.setBillingMetricsConfiguration(billingConfig); 
   mediaPlayer.replaceCurrentResource(mediaResource, config);
   ```

