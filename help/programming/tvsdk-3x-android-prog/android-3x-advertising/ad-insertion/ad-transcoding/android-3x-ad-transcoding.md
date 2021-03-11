---
description: 一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTP Live Streaming(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。
title: Adobeクリエイティブ再パッケージ化サービス(CRS)を使用して、互換性のない広告を再パッケージ化する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Adobeクリエイティブ再パッケージ化サービス(CRS) {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}を使用して、互換性のない広告を再パッケージ化

一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTP Live Streaming(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。

エージェンシー広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロードMP4形式など、互換性のない形式で配信されます。

TVSDKが互換性のない広告を初めて検出したとき、プレイヤーはその広告を無視し、Primetime広告挿入バックエンドの一部であるCreative Repackaging Service(CRS)に対して、互換性のある形式に広告を再パッケージ化するよう要求します。 CRSは、広告の複数のビットレートM3U8レンディションを生成し、これらのレンディションをPrimetime Content Network(CDN)に保存します。 次回TVSDKがその広告を指す広告レスポンスを受け取ると、プレイヤーはCDNからHLS互換のM3U8バージョンを使用します。

このオプションのCRS機能をアクティブにするには、Adobeの担当者にお問い合わせください。

>[!NOTE]
>
>CRS Version 3.0（およびそれ以前）のお客様は、CRS Version 3.1以降、セキュリティとパフォーマンスの両方を改善しました。
>
>* 再パッケージ化するコンテンツで`https:`が使用される場合、CRS 3.1は`https:`で続行します。 これにより、一部のプレーヤーで、セキュリティで保護されていないコンテンツが表示される可能性が低くなります。
   >
   >
* CRS 3.1は、ネットワーク呼び出しを大幅に最小化し、ビデオの起動時間を改善します。

>



## TVSDKアプリケーションでのCRSの有効化{#enable-crs-in-tvsdk-applications}

TVSDKアプリケーションでCRSを有効にするには、Auditude設定で次の情報を設定する必要があります。

1. `AuditudeSettings`でCRSを有効にします。

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
