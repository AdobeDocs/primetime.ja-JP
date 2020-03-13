---
description: 広告挿入メタデータをカスタマイズできます。
seo-description: 広告挿入メタデータをカスタマイズできます。
seo-title: 広告挿入メタデータのカスタマイズ
title: 広告挿入メタデータのカスタマイズ
uuid: 047470d3-45bd-48be-82ce-4e9d9fe6ea10
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 広告挿入メタデータのカスタマイズ{#customize-ad-insertion-metadata}

広告挿入メタデータをカスタマイズできます。

1. 未解決のオポチュニティの広告メタデータのタイムアウトを設定します。

   このタイムアウトのデフォルト値は20秒です。
1. 値を10秒に変更するには、次のように入力します。

   ```js
   auditudeSettings.timeout = 10000; //this value is specified in milliseconds
   ```

   プロパ `timeout` ティはクラスで定義さ `AdvertisingMetadata` れ、このタイムアウトはクラスから派生するカスタム広告設定に対して設定で `AdvertisingMetadata` きます。 例えば、FreeWheelリゾルバーのカスタム設定を定義する場合、この設定を使用してデフォルトのタイムアウトを設定できます。

1. 手順2 `MediaPlayerItemConfig` の広告設定を使用して作成します。

   ```js
   var config = new AdobePSDK.MediaPlayerItemConfig(); 
   config.advertisingMetadata = auditudeSettings;
   ```

1. を呼び出す際は、この設定を使 `replaceCurrentResource` 用しま `MediaPlayer`す。

   ```js
   player.replaceCurrentResource(mediaResource, config);
   ```

