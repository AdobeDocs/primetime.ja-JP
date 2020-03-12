---
description: TVSDKは、HTTPS経由の安全な配信を導入します。
seo-description: TVSDKは、HTTPS経由の安全な配信を導入します。
seo-title: HTTPS経由の安全な配信
title: HTTPS経由の安全な配信
translation-type: tm+mt
source-git-commit: 4a2271fc481b37bb0a437091de6efe98fcb348d9

---


# HTTPS経由の安全な配信 {#secure-delivery-https}

Adobe Primetime TVSDKは、TVSDKからのすべての呼び出し(

* Auditude広告サーバーの呼び出し
* CRSリクエスト
* DRMライセンスの呼び出し
* ビデオ分析のPing
* 請求Ping

この機能を使用するには、上記の要求を提供するように設定されたサーバーでHTTPSがサポートされていることを確認します。

この新しい動作は、デフォルトでは有効になっていません。 次を使用して、 `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
