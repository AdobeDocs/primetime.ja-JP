---
description: ビデオとオーディオを連続的にダウンロードするのではなく、並行的にダウンロードすると、起動時の遅延が軽減されます。
title: 並行ダウンロード
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# 並列ダウンロード{#parallel-downloads}

ビデオとオーディオを連続的にダウンロードするのではなく、並行的にダウンロードすると、起動時の遅延が軽減されます。

並行ダウンロードを使用すると、ビデオオンデマンド(VOD)ファイルを再生し、サーバーからの使用可能な帯域幅使用量を最適化し、バッファーの実行不足状況に陥る確率を下げ、ダウンロードと再生の間の遅延を最小限に抑えることができます。

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

並行ダウンロードを行わないと、TVSDKはビデオセグメントに対するリクエストを発行し、ビデオセグメントが読み込まれた後、1つまたは2つのオーディオセグメントをリクエストします。 並行ダウンロードでは、オーディオとビデオのセグメントが同時にダウンロードされ、順番にはダウンロードされません。 また、接続が2つあり、セグメントごとに2つのHTTP要求が並行して発生するので、データはより高速に画面に到達します。

>[!NOTE]
>
>この機能は、オーディオとビデオが異なるファイル（無変数のコンテンツ）にエンコードされるコンテンツにのみ適用され、MP4コンテンツ（常に無効なコンテンツ）には適用されません。 HLSコンテンツは、多くの場合、ミュート解除されます。特に代替オーディオの場合は、無効です。

<!-- 

See comment above (DASH use case removed).

  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
-->

HTTP接続では、次の段階で遅延が発生する場合があります。

* サーバーへのTCP/IP接続を確立する場合

   クライアントとサーバーは通信に同意しましたが、HTTP通信はまだ行われていません。 このタイプの遅延は、クライアントとサーバーの間のインフラストラクチャによって異なります。 このプロセスでは、クライアントとサーバーの間のインターネット経由のパスを見つけ、ルーターやファイアウォールなど、ルート上のすべてのデバイスがデータ転送に同意していることを確認する必要があります。
* TCP/IP接続を介してセグメントまたはマニフェストのHTTP要求を送信する場合。

   サーバーは要求を受け取り、処理し、データをクライアントに返送する開始を行います。 遅延の程度は、サーバーでのソフトウェアの読み込みと複雑さ、およびクライアントが要求を送信する際のアップロード接続速度によって異なります。