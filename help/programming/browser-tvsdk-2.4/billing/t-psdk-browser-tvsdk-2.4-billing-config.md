---
description: デフォルトの設定を使用する場合、課金を有効にしたり設定したりするために必要な操作は他にありません。 Adobeイネーブルメント担当者から異なる設定パラメーターを取得した場合は、 BillingMetricsConfiguration クラスを使用して、メディアプレーヤーを初期化する前にこれらのパラメーターを設定します。
title: 請求指標の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# 請求指標の設定{#configure-billing-metrics}

デフォルトの設定を使用する場合、課金を有効にしたり設定したりするために必要な操作は他にありません。 Adobeイネーブルメント担当者から異なる設定パラメーターを取得した場合は、 BillingMetricsConfiguration クラスを使用して、メディアプレーヤーを初期化する前にこれらのパラメーターを設定します。

ほとんどのお客様は、デフォルト設定を使用する必要があります。

>[!IMPORTANT]
>
>設定した設定は、メディアプレーヤーの存続期間中も有効です。 メディアプレーヤーを初期化した後は、設定を変更できません。

請求指標を設定するには、次の手順に従います。

* 次のコードサンプルを入力します。

  ```js
  var config = new AdobePSDK.MediaPlayerItemConfig(); 
  config.billingMetricsConfiguration.isEnabled = true; 
  config.billingMetricsConfiguration.proVODBillableDurationMinutes = 60; 
  config.billingMetricsConfiguration.stdVODBillableDurationMinutes = 30; 
  config.billingMetricsConfiguration.liveBillableDurationMinutes = 15; 
  _player.replaceCurrentResource(_resource, config);
  ```

  場所 `_player` は、 `AdobePSDK.MediaPlayer` および `_resource` は、 `AdobePSDK.MediaResource`.
