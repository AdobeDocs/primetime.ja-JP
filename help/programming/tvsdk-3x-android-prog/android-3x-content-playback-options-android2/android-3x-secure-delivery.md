---
description: TVSDKは、HTTPS経由の安全な配信を導入しています。
title: HTTPS経由の安全な配信
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---


# HTTPSを介したセキュア配信{#secure-delivery-https}

Adobe PrimetimeTVSDKは、TVSDKから派生するすべての呼び出し(

* Auditude広告サーバーの呼び出し
* CRSリクエスト
* DRMライセンスの呼び出し
* ビデオ分析のPing
* 請求PING

この機能を使用するには、上記の要求を処理するように設定されたサーバーでHTTPSがサポートされていることを確認してください。

この新しい動作は、デフォルトでは有効になっていません。 `MediaPlayer.replaceCurrentResource()`を呼び出す前に、次を使用してセキュリティで保護された配信を有効にします

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
