---
description: 302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。
title: 302 リダイレクトの最適化を無効または有効にします
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# HTTP 302 リダイレクトの最適化 {#http-302-redirect-optimization}

302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。

メインのマニフェストリクエストがリダイレクトされ、プレーヤーで 302 最適化が有効になっている場合、そのマニフェストからのアセットに対して以降におこなわれるリクエストでは最終的なドメインの場所が使用され、302 件の追加の応答が避けられます。

この機能はデフォルトで有効になっており、この設定は変更できます。

## 302 リダイレクトの最適化を無効または有効にします{#disable-or-enable-redirect-optimization}

以下を使用します。 `useRedirectedUrl` プロパティを使用して、302 リダイレクトをオン (true) またはオフ (false) にします。
例：

```java
// Set useRedirectedUrl property to false 
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.setUseRedirectedUrl(false); 
 
//Set NetworkConfiguration as Metadata: 
MetadataNode resourceMetadata = new MetadataNode();  
resourceMetadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(),  
                         networkConfiguration); 
 
//Call MediaResource.createFromURL to set the metadata: 
MediaResource resource = MediaResource.createFromURL(url, resourceMetadata); 
  
//Load the resource 
mediaPlayer.replaceCurrentItem(resource);
```
