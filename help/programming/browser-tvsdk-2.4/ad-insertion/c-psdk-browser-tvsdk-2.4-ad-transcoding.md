---
description: 一部のサードパーティ広告（またはクリエイティブ）は、ビデオ形式が HLS/DASH と互換性がないので、HTTP Live Streaming(HLS)/Dynamic Adaptive Streaming over HTTP(DASH) コンテンツストリームに結び付けることができません。 Adobe Primetime Ad Insertion と Browser TVSDK では、オプションで、互換性のないビデオを互換性のある m3u8/mpd ビデオに再パッケージ化（コード変換）しようとすることができます。
title: 互換性のない広告を再パッケージ化（トランスコード）
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 互換性のない広告を再パッケージ化（トランスコード）{#repackage-transcode-incompatible-ads}

一部のサードパーティ広告（またはクリエイティブ）は、ビデオ形式が HLS/DASH と互換性がないので、HTTP Live Streaming(HLS)/Dynamic Adaptive Streaming over HTTP(DASH) コンテンツストリームに結び付けることができません。 Adobe Primetime Ad Insertion と Browser TVSDK では、オプションで、互換性のないビデオを互換性のある m3u8/mpd ビデオに再パッケージ化（コード変換）しようとすることができます。

代理店広告サーバー、在庫パートナー、広告ネットワークなど、様々なサードパーティから提供される広告は、多くの場合、プログレッシブダウンロード MP4 など、互換性のない形式で配信されます。
