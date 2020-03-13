---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-title: HTTP 302リダイレクトの最適化
title: HTTP 302リダイレクトの最適化
uuid: 4bee0555-ae46-47c1-a067-206ad7ca8883
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# HTTP 302リダイレクトの最適化 {#http-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。

メインマニフェスト要求がリダイレクトされ、302最適化がプレイヤーで有効になっている場合、そのマニフェストからのアセットに対する後続の要求は最終的なドメインの場所を使用し、302個の応答が追加されるのを防ぎます。 この機能はデフォルトで有効になっており、この設定を変更できます。

## 302リダイレクトの最適化の無効化または有効化 {#section_8977448B268E41D69A8F75B60EB9DA3B}

302リダイレクト `useRedirectedUrl` のオン()またはオフ( `true`)を切り替えるには、このプロパティを使 `false`用します。

<!--<a id="example_888749F70C8A43279D06A29BD68E7E4D"></a>-->

例：

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration on MediaPlayerItemConfig 
MediaPlayerItemConfig config = new MediaPlayerItemConfig (); 
config.setNetworkConfiguration(networkConfiguration); 
 
//Use this config when loading the MediaPlayerItem or calling replaceCurrentResource
```

