---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
seo-title: HTTP 302リダイレクトの最適化
title: HTTP 302リダイレクトの最適化
uuid: d3009c6c-320a-4c0f-b6ba-bf6473049823
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---


# HTTP 302リダイレクトの最適化{#http-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。

メインのマニフェスト要求がリダイレクトされ、プレイヤーで302最適化が有効になっている場合、そのマニフェストからアセットに対して行われる以降の要求では、最終的なドメインの場所が使用され、302個の追加の応答が回避されます。 この機能はデフォルトで有効になっており、この設定は変更できます。

>[!IMPORTANT]
>
>この機能は、`XMLHttpRequest`オブジェクトの`responseURL`プロパティをサポートする認証済みブラウザーでのみサポートされます。

Flashのフォールバックの場合、次の情報に注意してください。

* エンドユーザーには、AdobeFlash Playerバージョン23以降がインストールされている必要があります。
* ストリームの整合性が無効になっている場合、302リダイレクトは認証済みブラウザーでのみサポートされます。

## 302リダイレクトの最適化を無効にしています{#disabling-redirect-optimization}

302リダイレクトを有効(true)または無効(false)にするには、useRedirectedUrlプロパティを使用します。

例：

```js
var networkConfiguration = new AdobePSDK.NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = false; 
 
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.networkConfiguration = networkConfiguration;; 
 
player.replaceCurrentResource(mediaResource, config);
```
