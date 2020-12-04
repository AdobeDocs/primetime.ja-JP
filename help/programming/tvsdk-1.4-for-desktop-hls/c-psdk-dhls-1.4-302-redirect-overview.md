---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。
seo-title: HTTP 302リダイレクトの最適化
title: HTTP 302リダイレクトの最適化
uuid: 58593d5f-a639-4d87-9589-dba6b2dbba38
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# HTTP 302リダイレクトの最適化{#http-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行うことができます。

メインのマニフェスト要求がリダイレクトされ、プレイヤーで302最適化が有効になっている場合、そのマニフェストからアセットに対して行われる以降の要求では、最終的なドメインの場所が使用され、302個の追加の応答が回避されます。

この機能はデフォルトで無効になっています。この設定は変更できます。

この機能を有効にした場合、次の条件の&#x200B;*すべて*&#x200B;が真の場合にのみ、正しく機能します。それ以外の場合は、リダイレクトの最適化は行われず、302応答が引き続き発生します。

* AdobeFlash Player11.8用に`-swf-version` 21以上を使用してコンパイルされました。
* エンドユーザーにはAdobeFlash Player11.8以降がインストールされています。

>[!IMPORTANT]
>
>cookieが広告リクエストで渡されるようにするには、302リダイレクトを無効にします。 302リダイレクトが有効な場合、cookieの作成元とは異なるドメインに広告リクエストがリダイレクトされる可能性があります。

## 302リダイレクトの最適化を無効または有効にする{#section_D6687FC44C61446F878008B629A5FA19}

`useRedirectedUrl`プロパティを使用して、302リダイレクトを有効(true)または無効(false)にします。

<!--<a id="example_B886777252B745AAB48B1FCC42C97A25"></a>-->

例：

```
// Set useRedirectedUrl property to true 
var networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = true; 
  
//Set NetworkConfiguration as Metadata: 
var result:Metadata = new Metadata(); 
result.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                   networkConfiguration); 
  
var mediaResource = new MediaResource( url, MediaResourceType.HLS, result); 
  
// load the resource 
mediaPlayer.replaceCurrentResource( mediaResource, mediaPlayerItemConfig );
```

