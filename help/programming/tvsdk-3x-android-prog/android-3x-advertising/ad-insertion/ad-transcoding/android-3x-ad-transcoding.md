---
description: 一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTPライブストリーミング(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。
seo-description: 一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTPライブストリーミング(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。
seo-title: Adobe Creative Repackaging Service(CRS)を使用して、互換性のない広告を再パッケージ化する
title: Adobe Creative Repackaging Service(CRS)を使用して、互換性のない広告を再パッケージ化する
uuid: ef542d13-6d52-4429-8a1e-0af2df236f12
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Adobe Creative Repackaging Service(CRS)を使用して、互換性のない広告を再パッケージ化する {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

一部のサードパーティの広告（またはクリエイティブ）は、ビデオ形式がHLSと互換性がないので、HTTPライブストリーミング(HLS)コンテンツストリームに繋ぎ合わせることができません。 Primetime広告の挿入とTVSDKは、オプションで、互換性のない広告を互換性のあるM3U8ビデオに再パッケージ化することができます。

エージェンシー広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロードMP4形式など、互換性のない形式で配信されます。

TVSDKが最初に互換性のない広告を見つけたとき、プレイヤーはその広告を無視し、Primetime広告挿入バックエンドの一部であるクリエイティブ再パッケージ化サービス(CRS)に対して、互換性のある形式に広告を再パッケージ化する要求を発行します。 CRSは、広告の複数のビットレートM3U8レンディションを生成し、これらのレンディションをPrimetime Content Delivery Network(CDN)に保存しようとします。 次回TVSDKがその広告を指す広告応答を受け取ると、プレイヤーはCDNからHLS互換のM3U8バージョンを使用します。

このオプションのCRS機能をアクティブにするには、アドビの担当者にお問い合わせください。

>[!NOTE]
>
>CRSバージョン3.0（およびそれ以前）のお客様の場合、CRSバージョン3.1以降、次の変更によりセキュリティとパフォーマンスの両方が向上しました。>
>* CRS 3.1は、再パッケージ化されるコンテ `https:` ンツが使用されている場合に続行しま `https:`す。 これにより、一部のプレーヤーが安全でないコンテンツを表示する可能性が低下します。
   >
   >
* CRS 3.1は、ネットワーク呼び出しを大幅に最小化し、ビデオの起動時間を改善します。
>



CRSについて詳しくは、 [Creative Packaging Service(CRS)を参照してください](../../../../../dynamic-ad-insertion/creative-repackaging-service/crs-overview.md)。

## TVSDKアプリケーションでのCRSの有効化 {#enable-crs-in-tvsdk-applications}

TVSDKアプリケーションでCRSを有効にするには、Auditudeの設定で次の情報を設定する必要があります。

1. でCRSを有効にしま `AuditudeSettings`す。

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
