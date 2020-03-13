---
description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-description: 302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。
seo-title: HTTP 302リダイレクトの最適化
title: HTTP 302リダイレクトの最適化
uuid: 58593d5f-a639-4d87-9589-dba6b2dbba38
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# HTTP 302リダイレクトの最適化{#http-redirect-optimization}

302リダイレクトの最適化は、302リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランシングをより効果的に行えるようにします。

メインマニフェスト要求がリダイレクトされ、302最適化がプレイヤーで有効になっている場合、そのマニフェストからのアセットに対する後続の要求は最終的なドメインの場所を使用し、302個の応答が追加されるのを防ぎます。

この機能はデフォルトで無効になっており、この設定を変更できます。

この機能を有効にした場合、次の条件のすべてが真 *である* 場合にのみ正しく機能します。それ以外の場合、リダイレクトの最適化は行われず、302応答が引き続き発生します。

* アプリケーションが21以上を使用してAdobe Flash Player 11.8用にコンパイルさ `-swf-version` れている。
* エンドユーザーにAdobe Flash Player 11.8以降がインストールされている。

>[!IMPORTANT]
>
>Cookieが広告リクエストで渡されるようにするには、302リダイレクトを無効にします。 302リダイレクトが有効な場合、Cookieの送信元のドメインとは異なるドメインに広告リクエストがリダイレクトされる可能性があります。

## 302リダイレクトの最適化の無効化または有効化 {#section_D6687FC44C61446F878008B629A5FA19}

302リダイレクト `useRedirectedUrl` をオン(true)またはオフ(false)にするには、このプロパティを使用します。

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

