---
description: 一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTP Live Streaming(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。
title: Adobeクリエイティブの再パッケージングサービスを使用して、互換性のない広告を再パッケージ化する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---


# Adobeクリエイティブ再パッケージングサービス{#repackage-incompatible-ads-using-adobe-creative-repackaging-service}を使用して、互換性のない広告を再パッケージ化する

一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTP Live Streaming(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。

エージェンシー広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロードMP4など、互換性のない形式で配信されます。

TVSDKが互換性のない広告を初めて検出したとき、プレイヤーはその広告を無視し、Primetime広告挿入バックエンドの一部であるCreative Repackaging Service(CRS)に対して、互換性のある形式に広告を再パッケージ化するよう要求します。 CRSは、広告のマルチビットレートM3U8レンディションを生成し、これらのレンディションをPrimetime Content Network(CDN)に保存します。 次回TVSDKがその広告を指す広告レスポンスを受け取ると、プレイヤーはCDNからHLS互換のM3U8バージョンを使用します。

このオプション機能を有効にするには、Adobeの担当者にお問い合わせください。

CRSについて詳しくは、[Creative Packaging Service(CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf)を参照してください。

## CRS広告配信{#multiple-cdn-support-for-crs-ad-delivery}の複数CDNのサポート

デフォルトのCreative Repackaging Service(CRS)シナリオでは1つのContent Data Network(CDN)を使用しますが、CRSアセットは複数のCDNにデプロイできます。

次の理由で、複数のCDNを使用できます。

* 大きな表示イベントに対して拡大する必要がある。
* CRSアセットのCDNソースとメインコンテンツのCDNソースを一致させる必要がある。

TVSDK URL Transformer APIを使用して、CRSが提供するデフォルトのURLを変換できます。

TVSDKに追加されたAPIを次に示します。

* `URLTransformer` TVSDKがリクエストするCRS広告URLの変換に必要なメソッドを記述するインターフェイス。アプリケーションは、このインターフェイスを実装し、必要なメソッドの実装を提供できます。

* `DefaultURLTransformer` TVSDKで作成され、インター `URLTransformer` フェイスを実装する、デフォルトのURLトランスフォーマーインスタンスです。アプリケーションは、このクラスを上書きしたり、URL後の変換ハンドラーを追加したりできます。 このハンドラーは、デフォルトの変換が適用された後に、アプリケーションがURLリクエストに変更を加える場合に役立ちます。

* `NetworkConfiguration.setURLTransformer`  `NetworkConfiguration` 実装を設定するために `URLTransformer` メタデータインスタンスで提供されるsetterメソッド。

>[!IMPORTANT]
>
>アプリの実装では、`URLTransformerInputType`定義済みリストを確認し、CRSのタイプ`URLTransformerInputType.CRSCreative`の変換URLのみを確認する必要があります。

次のコードの例は、アプリケーションがデフォルトのホストコンポーネントを別の文字列（例：`cdn.mycrsdomain.com`）に変更する方法を示しています。

```java
NetworkConfiguration networkConfiguration = new NetworkConfiguration(); 
DefaultURLTransformer urlTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(new DefaultURLTransformer.URLTransformHandler() { 
    @Override 
    public String call(String url, URLTransformerInputType type) { 
        if (type == URLTransformerInputType.CRSCreative) { 
            try { 
                return url.replaceAll(new java.net.URI(url).getHost(), "cdn.mycrsdomain.com"); 
            } catch (URISyntaxException e) { 
            } 
        } 
        return url; 
    } 
}); 
   
networkConfiguration.setURLTransformer(urlTransformer); 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setNode(DefaultMetadataKeys.NETWORK_CONFIGURATION.getValue(), networkConfiguration);
```
