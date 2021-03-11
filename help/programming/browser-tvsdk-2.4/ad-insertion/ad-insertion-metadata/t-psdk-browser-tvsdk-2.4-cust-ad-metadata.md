---
description: 広告挿入メタデータをカスタマイズできます。
title: 広告挿入メタデータのカスタマイズ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# 広告挿入メタデータのカスタマイズ{#customize-ad-insertion-metadata}

広告挿入メタデータをカスタマイズできます。

1. 未解決のオポチュニティの広告メタデータにタイムアウトを設定します。

   このタイムアウトのデフォルト値は20秒です。
1. 値を10秒に変更するには、次のように入力します。

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   `timeout`プロパティは`AdvertisingMetadata`クラスで定義されており、このタイムアウトは`AdvertisingMetadata`クラスから派生するカスタム広告設定に対して設定できます。 例えば、FreeWheelリゾルバーのカスタム設定を定義する場合、この設定を使用してデフォルトのタイムアウトを設定できます。

1. 手順2の広告設定で`MediaPlayerItemConfig`を作成します。

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. `MediaPlayer`で`replaceCurrentResource`を呼び出す場合は、この設定を使用します。

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

