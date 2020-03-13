---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-title: 302リダイレクトの最適化の無効化または有効化
title: 302リダイレクトの最適化の無効化または有効化
uuid: 7561839f-aec6-4a59-a07a-7e4fa043fdc2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# HTTP 302リダイレクトの最適化 {#http-302-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。

メインマニフェスト要求がリダイレクトされ、302最適化がプレイヤーで有効になっている場合、そのマニフェストからのアセットに対する後続の要求は最終的なドメインの場所を使用し、302個の応答が追加されるのを防ぎます。

この機能はデフォルトで有効になっており、この設定を変更できます。

## 302リダイレクトの最適化の無効化または有効化{#disable-or-enable-redirect-optimization}

302リダイレクト `useRedirectedUrl` をオン(true)またはオフ(false)にするには、このプロパティを使用します。
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

