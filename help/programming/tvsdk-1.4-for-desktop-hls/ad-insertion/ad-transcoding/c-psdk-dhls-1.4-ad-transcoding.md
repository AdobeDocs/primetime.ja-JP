---
description: 一部のサードパーティ広告（またはクリエイティブ）は、ビデオ形式が HLS と互換性がないので、HTTP Live Streaming(HLS) コンテンツストリームに結合できません。 Primetime 広告の挿入と TVSDK は、オプションで、互換性のない広告を互換性のある M3U8 ビデオに再パッケージ化しようと試みます。
title: Creative Repackaging Service を使用して互換性のないAdobeを再パッケージ化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Creative Repackaging Service を使用して互換性のないAdobeを再パッケージ化 {#repackage-incompatible-ads-using-adobe-creative-repackaging-service}

一部のサードパーティ広告（またはクリエイティブ）は、ビデオ形式が HLS と互換性がないので、HTTP Live Streaming(HLS) コンテンツストリームに結合できません。 Primetime 広告の挿入と TVSDK は、オプションで、互換性のない広告を互換性のある M3U8 ビデオに再パッケージ化しようと試みます。

代理店広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロード MP4 など、互換性のない形式で配信されます。

TVSDK が互換性のない広告を初めて検出した場合、プレーヤーはその広告を無視し、Primetime 広告挿入バックエンドの一部であるクリエイティブ再パッケージ化サービス (CRS) に対して、互換性のある形式に広告を再パッケージ化するリクエストを発行します。 CRS は、広告のマルチビットレート M3U8 レンディションを生成し、これらのレンディションを Primetime コンテンツ配信ネットワーク (CDN) に保存しようとします。 次に TVSDK がその広告を指す広告応答を受け取ると、プレーヤーは CDN から HLS 互換の M3U8 バージョンを使用します。

このオプション機能を有効にするには、Adobe担当者にお問い合わせください。

CRS について詳しくは、 [クリエイティブパッケージングサービス (CRS)](https://helpx.adobe.com/content/dam/help/en/primetime/guides/crs.pdf).

## CRS 広告配信の複数の CDN サポート {#multiple-cdn-support-for-crs-ad-delivery}

Creative Repackaging Service(CRS) のデフォルトのシナリオでは 1 つのコンテンツデータネットワーク (CDN) を使用しますが、CRS アセットを複数の CDN にデプロイできます。

次の理由により、複数の CDN を使用できます。

* 大規模な表示イベントに対して拡大する必要がある。
* CRS アセットの CDN ソースとメインコンテンツの CDN ソースを一致させるための要件。

TVSDK URL Transformer API を使用して、CRS が提供するデフォルト URL を変換できます。

TVSDK に API を追加しました。

* `URLTransformer` TVSDK がリクエストした CRS 広告 URL の変換に必要なメソッドを記述するインターフェイス。 アプリケーションは、このインターフェイスを実装し、必要なメソッドの実装を提供できます。

* `DefaultURLTransformer` TVSDK で作成され、を実装するデフォルトの URL 変換サービスインスタンス。 `URLTransformer` インターフェイス。 アプリケーションは、このクラスを上書きしたり、URL 変換後のハンドラーを追加したりできます。 このハンドラーは、デフォルトの変換が適用された後に、アプリケーションが URL リクエストに変更を加える場合に役立ちます。

* `NetworkConfiguration.urlTransformer` セッターメソッドは、 `NetworkConfiguration` 設定するメタデータインスタンス `URLTransformer` 実装。

>[!IMPORTANT]
>
>アプリの実装では、 `URLTransformerInputType` 列挙とタイプの変換 URL のみ `URLTransformerInputType.CRSCreative` CRS.

次のコードサンプルは、アプリケーションがデフォルトのホストコンポーネントを別の文字列 ( 例えば、 `cdn.mycrsdomain.com`):

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
