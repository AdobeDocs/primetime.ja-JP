---
description: マニフェストのダウンロード時にネットワーク接続状態を無視するよう TVSDK に指示する新しい API が導入されました。
title: Android でのオフライン再生
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Android でのオフライン再生 {#offline-playback-with-android}

マニフェストのダウンロード時にネットワーク接続状態を無視するよう TVSDK に指示する、次の API が導入されました。 通常、ネットワーク接続状態は、フォールバックを試みるか、ネットワークの再開を待つかを決定するために、アダプティブビットレートストリーミング (ABR) 中に使用されます。

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

この設定を有効にして、ネットワーク接続を無視することができます。

設定 `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` を true に設定します。 ブール値のデフォルト値は false です。

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
