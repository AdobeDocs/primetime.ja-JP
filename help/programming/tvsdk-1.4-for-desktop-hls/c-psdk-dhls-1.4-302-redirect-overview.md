---
description: 302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。
title: HTTP 302 リダイレクトの最適化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# HTTP 302 リダイレクトの最適化{#http-redirect-optimization}

302 リダイレクトの最適化により、302 リダイレクト応答の数を最小限に抑え、アプリケーションのロードバランスをより効果的に実現できます。

メインのマニフェストリクエストがリダイレクトされ、プレーヤーで 302 最適化が有効になっている場合、そのマニフェストからのアセットに対して以降におこなわれるリクエストでは最終的なドメインの場所が使用され、302 件の追加の応答が避けられます。

この機能はデフォルトで無効になっています。この設定は変更できます。

この機能を有効にした場合、正しく機能するのは、 *すべて* 以下の条件のうち、真の場合。それ以外の場合、リダイレクトの最適化はおこなわれず、302 応答は引き続き発生します。

* アプリケーションは、次を使用してAdobeFlash Player11.8 用にコンパイルされました。 `-swf-version` 21 以上。
* エンドユーザーには、AdobeFlash Player11.8 以降がインストールされています。

>[!IMPORTANT]
>
>Cookie が広告リクエストと共に渡されるようにするには、302 リダイレクトを無効にします。 302 リダイレクトが有効になっている場合、Cookie が生成されたドメインとは異なるドメインに広告リクエストがリダイレクトされることがあります。

## 302 リダイレクトの最適化を無効または有効にします {#section_D6687FC44C61446F878008B629A5FA19}

以下を使用します。 `useRedirectedUrl` プロパティを使用して、302 リダイレクトをオン (true) またはオフ (false) にします。

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
