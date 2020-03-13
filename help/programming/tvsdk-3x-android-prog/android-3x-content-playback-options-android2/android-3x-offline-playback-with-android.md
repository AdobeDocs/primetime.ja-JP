---
description: 'マニフェストのダウンロード時にネットワーク接続状態を無視するようTVSDKに指示する新しいAPIが導入されました。 '
seo-description: 'マニフェストのダウンロード時にネットワーク接続状態を無視するようTVSDKに指示する新しいAPIが導入されました。 '
seo-title: Androidでのオフライン再生
title: Androidでのオフライン再生
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Androidでのオフライン再生 {#offline-playback-with-android}

マニフェストのダウンロード時にネットワーク接続状態を無視するようTVSDKに指示する次のAPIが導入されました。 ネットワーク接続状態は、通常、アダプティブビットレートストリーミング(ABR)中に、フォールバックを試みるか、ネットワークの再開を待つかを決定するために使用されます。

```
NetworkConfiguration::setOfflinePlayback(boolean)
boolean NetworkConfiguration::getOfflinePlayback()
```

この設定を有効にして、ネットワーク接続を無視することができます。

trueに設 `com.adobe.mediacore.system.NetworkConfiguration::setOfflinePlayback` 定します。 ブール値のデフォルト値はfalseです。

```
// example of NetworkConfiguration
// wherever you currently set up MediaResource and MediaPlayerItemConfig
NetworkConfiguration networkConfig = mediaPlayerItemConfig.getNetworkConfiguration();
networkConfig.setOfflinePlayback(true);
mediaPlayerItemConfig.setNetworkConfiguration(networkConfig);
```
