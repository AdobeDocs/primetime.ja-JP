---
description: 302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。
title: HTTP 302 リダイレクトの最適化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# HTTP 302 リダイレクトの最適化 {#http-redirect-optimization}

302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。

メインのマニフェストリクエストがリダイレクトされ、プレーヤーで 302 最適化が有効になっている場合、そのマニフェストからのアセットに対して以降におこなわれるリクエストでは最終的なドメインの場所が使用され、302 件の追加の応答が避けられます。 この機能はデフォルトで有効になっており、この設定は変更できます。

>[!IMPORTANT]
>
>この機能は、 `responseURL` プロパティを `XMLHttpRequest` オブジェクト。

Flashフォールバックの場合、次の情報に留意してください。

* エンドユーザーには、AdobeFlash Playerバージョン 23 以降がインストールされている必要があります。
* ストリームの整合性が無効になっている場合、302 リダイレクトは認証済みブラウザーでのみサポートされます。

## 302 リダイレクトの最適化の無効化 {#disabling-redirect-optimization}

useRedirectedUrl プロパティを使用して、302 リダイレクトを有効 (true) にするか、無効 (false) にすることができます。

例：

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
