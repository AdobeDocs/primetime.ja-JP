---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
seo-title: 302リダイレクトの最適化の無効化または有効化
title: 302リダイレクトの最適化の無効化または有効化
uuid: 7561839f-aec6-4a59-a07a-7e4fa043fdc2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 1%

---


# HTTP 302リダイレクトの最適化{#http-302-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。

メインのマニフェスト要求がリダイレクトされ、プレイヤーで302最適化が有効になっている場合、そのマニフェストからアセットに対して行われる以降の要求では、最終的なドメインの場所が使用され、302個の追加の応答が回避されます。

この機能はデフォルトで有効になっており、この設定は変更できます。

## 302リダイレクトの最適化を無効または有効にする{#disable-or-enable-redirect-optimization}

`useRedirectedUrl`プロパティを使用して、302リダイレクトを有効(true)または無効(false)にします。
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

