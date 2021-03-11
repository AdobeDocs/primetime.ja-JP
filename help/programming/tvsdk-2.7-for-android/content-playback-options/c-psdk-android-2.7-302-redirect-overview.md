---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
title: HTTP 302リダイレクトの最適化
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---


# HTTP 302リダイレクトの最適化{#http-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。

メインのマニフェスト要求がリダイレクトされ、プレイヤーで302最適化が有効になっている場合、そのマニフェストからアセットに対して行われる以降の要求では、最終的なドメインの場所が使用され、302個の追加の応答が回避されます。 この機能はデフォルトで有効になっており、この設定は変更できます。

## 302リダイレクトの最適化を無効または有効にする{#section_8977448B268E41D69A8F75B60EB9DA3B}

302リダイレクトを有効(`true`)または無効(`false`)にするには、`useRedirectedUrl`プロパティを使用します。

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

