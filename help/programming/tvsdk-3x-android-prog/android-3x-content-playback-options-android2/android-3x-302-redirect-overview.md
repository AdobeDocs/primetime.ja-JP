---
description: 302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。
title: HTTP 302 リダイレクトの最適化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# HTTP 302 リダイレクトの最適化 {#http-redirect-optimization}

302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。

メインのマニフェストリクエストがリダイレクトされ、プレーヤーで 302 最適化が有効になっている場合、そのマニフェストからのアセットに対して以降におこなわれるリクエストでは最終的なドメインの場所が使用され、302 件の追加の応答が避けられます。 この機能はデフォルトで有効になっており、この設定は変更できます。

## 302 リダイレクトの最適化を無効または有効にします {#section_8977448B268E41D69A8F75B60EB9DA3B}

以下を使用します。 `useRedirectedUrl` 302 リダイレクトを有効にするプロパティ ( `true`) または off ( `false`) をクリックします。

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
