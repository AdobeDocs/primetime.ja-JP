---
description: TVSDK は、HTTPS を介したセキュアな配信を導入します。
title: HTTPS 経由でのセキュア配信
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# HTTPS 経由でのセキュア配信 {#secure-delivery-https}

Adobe Primetime TVSDK は、TVSDK からのすべての呼び出しに対して HTTPS 配信をサポートします。この配信には、以下が含まれます。

* Auditude広告サーバーコール
* CRS リクエスト
* DRM ライセンス呼び出し
* ビデオ分析の Ping
* 請求 ping

この機能を使用するには、上記のリクエストを処理するように設定されたサーバーが HTTPS をサポートしていることを確認します。

この新しい動作は、デフォルトでは有効になっていません。 次を使用して、への呼び出しの前にセキュア配信を有効にします。 `MediaPlayer.replaceCurrentResource()`

```java
MediaPlayerItemConfig config = new MediaPlayerItemConfig(context);
NetworkConfiguration netConfig  = new NetworkConfiguration();
netConfig.setForceHTTPS(true);
config.setNetworkConfiguration(netConfig);
```
