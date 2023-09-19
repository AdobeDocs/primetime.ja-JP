---
description: 広告挿入メタデータをカスタマイズできます。
title: 広告挿入メタデータのカスタマイズ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 広告挿入メタデータのカスタマイズ{#customize-ad-insertion-metadata}

広告挿入メタデータをカスタマイズできます。

1. 未解決のオポチュニティに対して、広告メタデータにタイムアウトを設定します。

   このタイムアウトのデフォルト値は 20 秒です。
1. 値を 10 秒に変更するには、次のように入力します。

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   The `timeout` プロパティが `AdvertisingMetadata` クラスに設定され、このタイムアウトは、 `AdvertisingMetadata` クラス。 例えば、FreeWheel リゾルバのカスタム設定を定義する場合、この設定を使用してデフォルトのタイムアウトを設定できます。

1. 作成 `MediaPlayerItemConfig` を、手順 2 の広告設定と共に使用します。

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. 呼び出し時にこの設定を使用 `replaceCurrentResource` オン `MediaPlayer`.

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```
