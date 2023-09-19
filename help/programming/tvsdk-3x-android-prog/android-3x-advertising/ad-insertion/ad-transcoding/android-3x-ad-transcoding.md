---
description: 一部のサードパーティ広告（またはクリエイティブ）は、ビデオ形式が HLS と互換性がないので、HTTP Live Streaming(HLS) コンテンツストリームに結合できません。 Primetime 広告の挿入と TVSDK は、オプションで、互換性のない広告を互換性のある M3U8 ビデオに再パッケージ化しようと試みます。
title: Creative Repackaging Service (CRS)Adobeを使用した、互換性のない広告の再パッケージ化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Creative Repackaging Service (CRS)Adobeを使用した、互換性のない広告の再パッケージ化 {#repackage-incompatible-ads-using-adobe-creative-repackaging-service-crs}

一部のサードパーティ広告（またはクリエイティブ）は、ビデオ形式が HLS と互換性がないので、HTTP Live Streaming(HLS) コンテンツストリームに結合できません。 Primetime 広告の挿入と TVSDK は、オプションで、互換性のない広告を互換性のある M3U8 ビデオに再パッケージ化しようと試みます。

代理店広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロード MP4 形式など、互換性のない形式で配信されます。

TVSDK が互換性のない広告を初めて検出した場合、プレーヤーはその広告を無視し、Primetime 広告挿入バックエンドの一部であるクリエイティブ再パッケージ化サービス (CRS) に対して、互換性のある形式に広告を再パッケージ化するリクエストを発行します。 CRS は、広告の複数のビットレート M3U8 レンディションを生成しようとし、これらのレンディションを Primetime コンテンツ配信ネットワーク (CDN) に保存します。 次に TVSDK がその広告を指す広告応答を受け取ると、プレーヤーは CDN から HLS 互換の M3U8 バージョンを使用します。

このオプションの CRS 機能をアクティブにするには、Adobe担当者にお問い合わせください。

>[!NOTE]
>
>CRS バージョン 3.0（およびそれ以前）のお客様は、CRS バージョン 3.1 以降、次の変更によりセキュリティとパフォーマンスの両方が向上しました。
>
>* CRS 3.1 は、 `https:` 再パッケージ化するコンテンツが `https:`. これにより、一部のプレーヤーが安全でないコンテンツを表示する可能性が低下します。
>
>* CRS 3.1 は、ネットワーク呼び出しを大幅に最小限に抑え、ビデオの起動時間を改善します。
>

## TVSDK アプリケーションでの CRS の有効化 {#enable-crs-in-tvsdk-applications}

TVSDK アプリケーションで CRS を有効にするには、Auditude設定で次の情報を設定する必要があります。

1. で CRS を有効にする `AuditudeSettings`.

   ```
   ... 
   auditudeSettings.setCreativeRepackagingEnabled(true); 
   auditudeSettings.setCreativeRepackagingFormat("application/x-mpegURL"); 
   ```
