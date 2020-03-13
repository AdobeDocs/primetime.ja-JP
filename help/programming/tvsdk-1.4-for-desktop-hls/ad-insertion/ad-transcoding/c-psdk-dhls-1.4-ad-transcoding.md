---
description: 一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTPライブストリーミング(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。
seo-description: 一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTPライブストリーミング(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。
seo-title: Adobe Creative Repackaging Serviceを使用して、互換性のない広告を再パッケージ化する
title: Adobe Creative Repackaging Serviceを使用して、互換性のない広告を再パッケージ化する
uuid: 3bc24185-6b19-4660-bf78-5ccdaf14787a
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Adobe Creative Repackaging Serviceを使用して、互換性のない広告を再パッケージ化する {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTPライブストリーミング(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。

エージェンシー広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロードMP4など、互換性のない形式で配信されます。

TVSDKが最初に互換性のない広告を見つけたとき、プレイヤーはその広告を無視し、Primetime広告挿入バックエンドの一部であるクリエイティブ再パッケージ化サービス(CRS)に対して、互換性のある形式に広告を再パッケージ化する要求を発行します。 CRSは、広告の複数ビットレートのM3U8レンディションを生成し、これらのレンディションをPrimetimeコンテンツ配信ネットワーク(CDN)に保存しようとします。 次回TVSDKがその広告を指す広告応答を受け取ると、プレイヤーはCDNからHLS互換のM3U8バージョンを使用します。

このオプション機能を有効にするには、アドビの担当者にお問い合わせください。

CRSについて詳しくは、 [Creative Packaging Service(CRS)を参照してください](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf)。

## CRS広告配信の複数CDNのサポート {#multiple-cdn-support-for-crs-ad-delivery}

デフォルトのCreative Repackaging Service(CRS)シナリオでは1つのContent Data Network(CDN)を使用しますが、CRSアセットは複数のCDNにデプロイできます。

次の理由で、複数のCDNを使用できます。

* 大きな表示イベントに対して拡大する必要がある。
* CRSアセットのCDNソースとメインコンテンツのCDNソースを一致させる必要がある。

CRSが提供するデフォルトのURLは、TVSDK URL Transformer APIを使用して変換できます。

TVSDKに追加されたAPIを次に示します。

* `URLTransformer` TVSDKが要求するCRS広告URLを変換するために必要なメソッドを記述するインターフェイス。 アプリケーションは、このインターフェイスを実装し、必要なメソッドの実装を提供できます。

* `DefaultURLTransformer` TVSDKで作成され、インターフェイスを実装する、デフォルトのURLトランスフォーマーインスタンス `URLTransformer` です。 アプリケーションは、このクラスを上書きしたり、URL後の変換ハンドラーを追加したりできます。 このハンドラーは、デフォルトの変換が適用された後に、アプリケーションがURLリクエストに変更を加える場合に役立ちます。

* `NetworkConfiguration.urlTransformer` 実装を設定するためにメタデータインスタ `NetworkConfiguration` ンスで提供されるsetterメソッ `URLTransformer` ドです。

>[!IMPORTANT]
>
>アプリの実装では、CRSのタイプの `URLTransformerInputType` 変換URLのみが列挙されているかどうかを確認する `URLTransformerInputType.CRSCreative` 必要があります。

次のコードの例は、アプリケーションがデフォルトのホストコンポーネントを別の文字列(例： `cdn.mycrsdomain.com`)に変更する方法を示しています。

```
var networkConfiguration:NetworkConfiguration = new NetworkConfiguration(); 
   
var urlTransformer:DefaultURLTransformer = new DefaultURLTransformer(); 
urlTransformer.addPostURLTransformHandler(function (url:String, type:String) { 
    if (type == URLTransformerInputType.CRSCreative) { 
        return url.replace(URLUtil.getServerName(url), "cdn.mycrsdomain.com"); 
    } 
    return url; 
}); 
  
networkConfiguration.urlTransformer = urlTransformer; 
   
// metadata is the Metadata instance set on a MediaResource instance. 
metadata.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                     networkConfiguration);
```
