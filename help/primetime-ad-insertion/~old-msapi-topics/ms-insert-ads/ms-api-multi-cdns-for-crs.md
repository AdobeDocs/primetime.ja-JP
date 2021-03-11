---
description: デフォルトのCreative Repackaging Service(CRS)シナリオでは1つのコンテンツ配信ネットワーク(CDN)を使用しますが、CRSアセットは複数のCDNにデプロイできます。
title: CRS広告配信の複数のCDNのサポート
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '189'
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

詳しくは、CRSドキュメントの[マルチCDNのサポート](../../~old-creative-repackaging-service/multi-cdn-supportt.md)を参照してください。
