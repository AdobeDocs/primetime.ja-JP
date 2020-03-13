---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-title: HTTP 302リダイレクトの最適化
title: HTTP 302リダイレクトの最適化
uuid: d3009c6c-320a-4c0f-b6ba-bf6473049823
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# HTTP 302リダイレクトの最適化 {#http-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。

メインマニフェスト要求がリダイレクトされ、302最適化がプレイヤーで有効になっている場合、そのマニフェストからのアセットに対する後続の要求は最終的なドメインの場所を使用し、302個の応答が追加されるのを防ぎます。 この機能はデフォルトで有効になっており、この設定を変更できます。

>[!IMPORTANT]
>
>この機能は、オブジェクトのプロパティをサポートする認証済みブラウザ `responseURL` ーでのみサポートさ `XMLHttpRequest` れます。

Flashフォールバックの場合は、次の情報に注意してください。

* エンドユーザーは、Adobe Flash Playerバージョン23以降がインストールされている必要があります。
* ストリームの整合性が無効な場合、302リダイレクトは認証済みブラウザーでのみサポートされます。

## 302リダイレクト最適化の無効化 {#disabling-redirect-optimization}

useRedirectedUrlプロパティを使用して、302リダイレクトを有効(true)または無効(false)にできます。

例：

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
