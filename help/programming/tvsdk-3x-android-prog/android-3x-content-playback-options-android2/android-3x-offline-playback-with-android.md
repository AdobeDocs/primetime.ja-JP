---
description: 'TVSDKに、マニフェストのダウンロード時にネットワーク接続状態を無視するよう指示する新しいAPIが導入されました。 '
seo-description: 'TVSDKに、マニフェストのダウンロード時にネットワーク接続状態を無視するよう指示する新しいAPIが導入されました。 '
seo-title: Androidでのオフライン再生
title: Androidでのオフライン再生
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---


# Android {#offline-playback-with-android}でのオフライン再生

TVSDKに、マニフェストのダウンロード時にネットワーク接続状態を無視するよう指示する以下のAPIが導入されました。 ネットワーク接続状態は、通常、アダプティブビットレートストリーミング(ABR)中に使用され、フォールバックを試行するか、ネットワークの再開を待つかを決定します。

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

この設定を有効にして、ネットワーク接続を無視できます。

`com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback`をtrueに設定します。 ブール値のデフォルト値はfalseです。

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
