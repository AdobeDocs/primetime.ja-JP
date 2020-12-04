---
description: デフォルトのCreative Repackaging Service(CRS)シナリオでは1つのコンテンツ配信ネットワーク(CDN)を使用しますが、CRSアセットは複数のCDNにデプロイできます。
seo-description: デフォルトのCreative Repackaging Service(CRS)シナリオでは1つのコンテンツ配信ネットワーク(CDN)を使用しますが、CRSアセットは複数のCDNにデプロイできます。
seo-title: CRS広告配信の複数のCDNのサポート
title: CRS広告配信の複数のCDNのサポート
uuid: c5557a38-aa49-4161-bb58-3e8dff9a4d64
translation-type: tm+mt
source-git-commit: f327b45de7e482dcb25407659846b2098f1fd49d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# CRS広告配信{#multiple-cdn-support-for-crs-ad-delivery}の複数CDNのサポート

デフォルトのCreative Repackaging Service(CRS)シナリオでは1つのコンテンツ配信ネットワーク(CDN)を使用しますが、CRSアセットは複数のCDNにデプロイできます。

## 要件

次の理由で、複数のCDNを使用できます。

* 大きな表示イベントに対して拡大する必要がある
* CRSアセットのCDNソースとメインコンテンツのCDNソースを一致させる必要がある。
* CRSのデフォルトCDN(Akamai)とは異なるCDNを使用する必要がある。

マニフェストサーバーは、トランスコードされた要求を参照する際に、多数のクエリパラメーターを含むブートストラップURLを使用します。 マルチCDN環境を設定した場合は、ブートストラップURLにも`ptcdn`パラメータを含める必要があります。 マニフェストサーバーは、このパラメーターを使用して、広告のトランスコードされたバージョンを取得するCDNサーバーを識別します。

詳しくは、CRSドキュメントの[マルチCDNのサポート](../../creative-repackaging-service/multi-cdn-supportt.md)を参照してください。
